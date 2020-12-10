# Paginacja, Filtrowanie

## Zadania

1. Dodaj widok oparty na GenericAPIView pozwalający na nawigację po API
2. Zamiast wartości kluczy obcych wstaw pole opisujące dany rekord (np. nazwisko, nazwa, tytuł) - użyj SlugRelatedField z klasy HyperlinkedModelSerializer
3. W związach jeden do wielu po stronie jeden wstaw linki do rekordów po stronie wiele - użyj HyperlinkedRelatedField z klasy HyperlinkedModelSerializer
4. Ustaw globalną paginację z liczbą pozycji na stronę 5
5. Ustaw filtry i sortowanie na poszczególne widoki
6. Dodaj własne filtry na datę i liczby jako przedział od - do
