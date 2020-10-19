# Serializacja danych

`Serializer` pozwala na konwersję złożonych danych na rodzime typy danych w języku Python, które można następnie łatwo przekształcić w JSON, XML lub inne typy treści. Serializatory zapewniają również deserializację, umożliwiając przekształcenie przeanalizowanych danych z powrotem w złożone typy po uprzednim sprawdzeniu poprawności danych przychodzących.

`Serializer` w środowisku REST działa bardzo podobnie do klas `Form` i `ModelForm` w Django. W naszych projektach będziemy korzystać z:

- `Serializer` - ogólny sposób kontrolowania requestów,
- `ModelSerializer` - sprawdzanie modeli, inicjalizacja.

Po dokładne informacje o serializacji odsyłamy do informacji z wykładu oraz [dokumentacji DRF](https://www.django-rest-framework.org/api-guide/serializers/).

## Przykład klasy do serializacji danych

```python
from rest_framework import serializers

class BlogPostSerializer(serializers.Serializer):
    title = serializers.CharField(max_length=100)
    content = serializers.CharField()

    def validate_title(self, value):
        """
        Check that the blog post is about Django.
        """
        if 'django' not in value.lower():
            raise serializers.ValidationError(
                "Blog post is not about Django",
            )
        return value
```

Zwróć uwagę, że funkcja odpowiedzialna za walidację danych jest w formacie `validate_{nazwa_pola}`.

# Ćwiczenia

Celem ćwiczeń będzie stworzenie klas odpowiedzialnych za serializację danych w naszym projekcie API. Następujące polecenia powinny być wykonane dla każdego modelu w projekcie, do którego będziemy mieli dostęp zewnętrzny (przez wykonanie endpointu, np. tworzenie zamówienia).

1. W **aplikacji**, w której znajduje się nasz model otwieramy/tworzymy plik `serializers.py`,
2. W nagłówku pliku dodajemy import:
   ```python
   from rest_framework import serializers
   ```
3. Tworzymy klasę dziedziczącą po `serializers.Serializer`, a następnie tworzymy odpowiednie pola, jako odpowiednik naszego modelu, które powinny zostać sprawdzone (praktycznie wszystkie, musimy sprawdzić czy przychodzące dane są dobrego typu np. do pola modelu z datą nie podajemy stringa z przepisem na barszcz).
4. Jeżeli dany model wymaga dodatkowej walidacji (np. data stworzenia zamówienia nie może być w przyszłości), tworzymy odpowiednie funkcje.
5. Nadpisujemy odpowiednie funkcje `create`, `update` itp. w momencie gdy musimy zapisać obiekty w inny sposób (np. chcemy dodać użytkownika jako właściciela stworzonego modelu).
6. Sprawdzamy, które z utworzonych serializerów możemy zamienić na `ModelSerializer`, i implementujemy gdy to możliwe ([Dokumentacja](https://www.django-rest-framework.org/api-guide/serializers/#modelserializer))