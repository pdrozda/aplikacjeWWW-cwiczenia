# TDD w Django

Przy składaniu podania rekrutacyjnego do dowolnej firmy informatycznej często pada pytanie, czy znasz magiczny termin TDD. Co to jest? Dowiedzmy się! TDD oznacza Test Driven Development i jest jedną z podstawowych filozofii tworzenia oprogramowania. Zobaczmy, co powie o tym wikipedia:

> Test Driven Development (TDD) to proces opracowywania oprogramowania, który polega na powtarzaniu bardzo krótkiego cyklu programowania: wymagania są przekształcane w bardzo konkretne przypadki testowe, a następnie oprogramowanie jest ulepszane, tak aby testy zakończyły się pomyślnie. Jest to przeciwieństwo tworzenia oprogramowania, które umożliwia dodawanie oprogramowania, które nie spełnia wymagań.

Brzmi fajnie, więc w zasadzie otrzymujemy działającą aplikację z funkcjami działającymi zgodnie z żądaniami… już po zakończeniu pisania kodu! To jest niesamowite. Jakie zatem kroki musimy podjąć, aby napisać projekt TDD?

1. Uzyskaj wymagania dotyczące nowej funkcji - należy je bardzo dobrze opisać (najlepiej przy użyciu user stories), abyś dokładnie wiedział, co powinna zrobić twoja funkcja / punkt końcowy / proces.
2. Napisz testy, które sprawdzą wszystko opisane w funkcji (co powinno zwrócić, jak obliczane są wartości itp.).
3. Uruchom testy, jeśli wszystkie nowe testy nie powiodą się, jesteś na dobrej drodze, aby zostać mistrzem TDD.
4. Napisz swój niesamowity kod, który wdroży tę funkcję.
5. Uruchom testy ponownie. Jeśli się nie uda, przejdź do punktu 4, w przeciwnym razie dobra robota! Wdrożyłeś swoją funkcję i jesteś uważany za najlepszego programistę w swoim zespole.
6. Refaktoryzacja jest zawsze dobrym pomysłem, nikt nie pisze doskonałego kodu przy pierwszej próbie. Przejrzyj kod i zobacz, co można poprawić. 
7. Zawsze dobrze jest ponownie uruchomić testy po tym kroku, aby sprawdzić, czy po drodze nie nastąpił błąd.

## Czemu pytest?
Pytest oferuje nowe podejście do pisania testów, oferując kilka schludnych rzeczy i pomocników:

- Assert’y budowane w inny sposób (nie musisz już używać self.assert),
- Świetna informacja, dlaczego dokładnie twój test się nie powiódł,
- Masz większą kontrolę nad Fixtures,
- Moduły testowe są automatycznie wykrywane,
- Parametryzacja, dzięki czemu możesz uruchomić wiele testów jednocześnie,
- Mniej zbędnego kodu,
- Dużo… i mam na myśli wiele… zewnętrznych wtyczek,
- I wiele więcej.


## Instalacja

Aby zainstalować pytest, użyjemy narzędzia polecenia pip. Zauważ, że nie instalujemy pytest w bazowej formie, ale opakowanie dla django o nazwie `pytest-django` (moduł podstawowy zostanie zainstalowany obok). Jedyne, czego potrzebujesz, aby napisać następujący wiersz w wybranym środowisku:

```
pip install pytest-django
```

Możesz opcjonalnie sprawdzić, czy zainstalowałeś poprawną wersję:

```
pytest --version
```

## Używanie pytest w projekcie django

Przede wszystkim musimy powiedzieć Django, że użyjemy pytest w naszym projekcie. Aby to zrobić, utwórz plik `pytest.ini` w katalogu głównym. Wypełnij go następującym kodem (oczywiście zamień `project_name` na swoją nazwę projektu):

```
[pytest]
DJANGO_SETTINGS_MODULE = project_name.settings
```

Możesz także określić plik ustawień jako zmienną środowiskową, co jest uważane za dobrą praktykę i umożliwia łatwe przełączanie ustawień. Ponadto, jeśli używasz niestandardowych nazw plików testowych (określone pliki lub symbole wieloznaczne), możesz dodać następujący wiersz:

```
python_files = test.py test_*.py *_test.py
```

Aby uruchomić testy, nie użyjesz `manage.py` jak w przypadku unittest. Teraz jest to trochę prostsze, domyślnym poleceniem jest:

```
pytest
```

Jeśli chcesz uruchomić określony katalog, plik lub funkcję, możesz to zrobić! Wystarczy wykonać jedną z poniższych czynności, zastępując nazwy tym, co masz:

```
pytest some_directory
pytest some_file.py
pytest some_file.py::your_function
```

## Gdzie umieścić testy

Teoretycznie… gdziekolwiek chcesz. W praktyce dobrze jest umieścić je w katalogu testów aplikacji Django. W ten sposób każda aplikacja ma własne miejsce do przechowywania testów. Ponadto możesz (i należy) podzielić testy na pliki, w zależności od tego, co testują, na przykład:

- `test_api.py` - do testowania punktów końcowych i tego, co jest zwracane,
- `test_services.py` - aby przetestować usługi zewnętrzne lub większe rzeczy w swoim projekcie,
- `test_models.py` - do testowania modeli,
- i tak dalej.

To zależy od twoich preferencji, ale dobrze jest zachować jeden wzór w całym projekcie.

## Testy API

Myślę, że możemy zacząć budować nasz zestaw testów dla projektu, który wykonujemy. Rozważ posiadanie modelu `Animal`, który jest częścią aplikacji `zoo`, model ma dwa pola `name` i `age`. Zamierzam napisać test dla funkcji, która sprawdza, czy model jest poprawnie zapisany, gdy uruchamiamy punkt końcowy na naszym interfejsie API django.

```python
# Importujemy pytest
import pytest

# Importujemy model
from zoo.models import Animal

# Piszemy fajną funkcję testową
# Użyjemy fixture authorized_client
def test__add_animal(authorized_client):
    # Dane które zapiszemy
    data_to_save = {
        'name': 'Wifi',
        'age': 4,
    }

    # Zakładając że endpoint wygląda tak:
    # POST localhost:8080/api/animals
    url = reverse('api:animals')

    # Wysyłamy dane
    response = authorized_client.post(
        url,
        data_to_save,
        content_type='application/json',
    )

    # Request się powiódł?
    assert response.status_code == 200

    # Czy odpowiedź nam odpowiada?
    assert response.json() == data_to_save

    # Czy został dodany obiekt?
    all_animals = Animal.objects.all()
    assert all_animals.count() == 1

    # Czy obiekt zapisał się poprawnie?
    saved_animal = all_animals.first()
    assert saved_animal.name == 'Wifi'
    assert saved_animal.age == 4
```

## Testy jednostkowe dla funkcji

Ale czasem masz bardziej skomplikowany punkt końcowy i tworzysz dodatkowe funkcje, które obliczają rzeczy, zbierają dane ze źródeł zewnętrznych lub cokolwiek innego. Dobrze byłoby oddzielić te testy dla struktury. Załóżmy, że mamy naprawdę fajną funkcję, która gromadzi ilość zwierząt na lądzie z zewnętrznego API. Mamy funkcję `get_quantity_from_external`, która pobiera odpowiedź i zwraca wartość dla `quantity`.

```python
# Znowu import
import pytest

# Importujemy funkcję
from zoo.services import get_quantity_from_external

# Zauważ że robimy patch na danych zewnętrznych
# Robimy to aby zamockować informacje z serwera
# By nie pobierać za każdym razem informacji
# Gdy wywołujemy test

@patch('zoo.services.external_function')
def test__get_quantity_from_function(
    external_function,  
):
    # Mockujemy odpowiedź z zewnątrz
    # Dane z National Geographic
    external_function.return_value = [
        {
            'animal': 'Great Elephant',
            'quantity': 352271,
            'region': 'Africa',
            'specie_range': 0.93,
        },
    ]

    # Odpalamy naszą funkcję!
    result = get_quantity_from_external('Great Elephant', 'Africa')
    assert result == 352271
    assert isinstance(result, int)

    # Sprawdźmy czy zwraca None gdy nie ma nic w bazie
    # Dzięki C.S.Lewis za to!
    result = get_quantity_from_external('Hnakra', 'Mars') 
    assert result == None
```

## Podsumowanie

Dzisiaj dowiedzieliśmy się kilku rzeczy. Jak zainstalować pytest (i dlaczego jest tak niesamowity), jak skonfigurować projekt django i uruchomić go, jak ustrukturyzować projekt pod kątem testów oraz jak pisać testy integracyjne i jednostkowe z przykładami. Oczywiście to nie jest cały temat, ale daje miłe wprowadzenie do tego, co ma nadejść. Aby uzyskać więcej informacji, naprawdę powinieneś sprawdzić oficjalną dokumentację.

Miłych testów!

## Zadanie

Stwórz testy jednostkowe oraz integracyjne dla swojego projektu API.
