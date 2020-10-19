# Wprowadzenie do języka Python

## Historia Python

Twórcą Pythona jest holender Guido van Rossum a sama nazwa, co niektórych zapewne nie dziwi, pochodzi od popularnego serialu BBC „Latający Cyrk Monty Pythona”. Prace nad pierwszym interpreterem Pythona rozpoczęły się w 1989 roku jako następca języka ABC. Wszystkie wersje aż do 1.2 powstawały w CWI (Centrum  Matematyki  i  Informatyki)  w  Amsterdamie gdzie Guido wówczas pracował. Od wersji 2.1Python był udostępniany jako projekt Open Source przez niedochodową organizację Python Software Foundation (PSF). Obecnie nad rozwojem Pythona pracuje wiele osób, ale Guido wciąż jest zaangażowany w ten proces.  Sam twórca w 1995 roku wyemigrował do USA gdzie w latach 2005 –2013 pracował dla Google a obecnie pracuje dla firmy Dropbox.

Ważnym momentem w historii Pythona było utworzenie drugiej głównej gałęzi – Pythona  3  w  roku 2008.  Od  tego  momentu  wersja  2 oraz 3 były rozwijane oddzielnie, ale czas wersji 2 zaczyna mijać o czym świadczy ogłoszony już termin zakończenia wsparcia na 12 kwietnia 2020 roku. Rozwój języka jest prowadzony przy wykorzystaniu PEP (Python Enhancement Proposal). Dokumenty te to propozycje rozszerzeń lub zmian w języku w postaci artykułu, który jest poddawany pod dyskusję wśród programistów Pythona. Każdy dokument zawiera  opis  proponowanego  rozwiązania, uzasadnienie  oraz  aktualny  status.  Po osiągnięciu  konsensusu propozycje są przyjmowane lub odrzucane.

## Wybrane cechy języka Python

Python jest językiem ogólnego przeznaczenia, którego ideą przewodnią jest czytelność i klarowność kodu źródłowego. Standardowa implementacja języka jest CPython (napisany w C), ale istnieją też inne, np. Jython (napisany w Javie), CLPython napisany w Common Lisp, IronPython (na platformę .NET) i PyPy napisany w Pythonie. Python nie wymusza jednego stylu programowania dając możliwość programowania obiektowego, programowania strukturalnego oraz programowania funkcyjnego.

**Inne cechy języka Python:**

- Typy sprawdzane są dynamicznie (w przeciwieństwie np. do Javy),
- Do zarządzania pamięcią używany jest garbage collector,
- Wszystkie wartości przekazywane są przez referencję,
- Jest czasem kwalifikowany jako język skryptowy,
- Nie ma enkapsulacji, jak to ma miejsce w C++ czy Javie, ale istnieją mechanizmy, które pozwalają na osiągnięcie podobnego efektu,
- Możliwe jest tworzenie funkcji ze zmienną liczbą argumentów,
- Możliwe jest tworzenie funkcji z argumentami o wartościach domyślnych.

## PyCharm Community Edition

W trakcie zajęć prezentacja przykładów kodu oraz ćwiczenia będą wykonywane z wykorzystaniem środowiska  PyCharm Community, którejest darmową wersją tego narzędzia. Wersja Community pozbawiona jest wielu udogodnień, które mogą przydaćsięna dalszym etapie pracy z językiem Python np. w trakcie wytwarzania  aplikacji  webowych  z  wykorzystaniem  m.in.  Django,  Flask,  JavaScript oraz  wielu  innych.  Mamy natomiast do dyspozycji „inteligentny” edytor, graficzny debugger, inspekcję kodu, wsparcie dla systemów kontroli wersji oraz pakiet narzędzi naukowych.

- [Bardziej szczegółowe porównanie Community vs Professional](https://www.jetbrains.com/pycharm/features/editions_comparison_matrix.html)

Firma  JetBrains,  która  jest  autorem  m.in.  oprogramowania  PyCharm  oferuje  pełen  pakiet oprogramowania w wersji Professional za darmo dla studentów oraz nauczycieli. Aby taką licencję uzyskać należy się zarejestrować i aplikować o przyznanie takiej licencji. Jedyne ograniczenie to wykorzystywanie tego oprogramowania do celów komercyjnych. 

- [Informacje o Professional dla studentów](https://www.jetbrains.com/student/)

## Organizacja kodu według PEP8

Jak zostało już wspomniane, w specyfikacji języka odbywają się poprzez system PEP. Dokument  o  numerze  PEP8  jest  jedną (ale nie jedyną) propozycją organizacji kodu języka Python. 

- [Oryginalna treść dokumentu PEP8](https://www.python.org/dev/peps/pep-0008/)

W dalszej części zajęć będziemy korzystać z `flake8`, aby dbać o jakość naszego kodu.

- [Więcej informacji o `flake8`](https://gitlab.com/pycqa/flake8)

### Wcięcia

 W kodzie języka Python nie znajdziemy znanych z PHP, Javy czy C# klamerek do separacji bloków kodu, określania ram ciała metody czy klasy lub zakresu operacji w pętli. Tutaj do tego celu służą odpowiednio ustawione wcięcia i puste linie między w/w elementami. Dla osób, które nigdy wcześniej nie miały do czynienia z taką organizacją kodu może to być zaskakujące, ale dość szybko staje się zrozumiałe i intuicyjne.

 ```python
 if score >= 100:
    print('Zwycięstwo !')
 ```

 Każdy  kolejny  poziom  zagnieżdżenia  w  bloku  kodu  poprzedza  odstęp  w  postaci wielokrotności  4  spacji (pojedyncza wartość wcięcia). Dopuszczalne jest również stosowanie tabulatorów jako wcięć, ale zalecane są spacje a dodatkowo w wersji Python 3 użycie jednocześnie spacji i tabulatorów jako wcięć nie jest dozwolone.

 Wcięcia używamy również w sytuacjach, w których linia kodu jest zbyt długa i musi być złamana na większą ilość wierszy. Zalecana długość linii według PEP8 to 79 znaków

 ```python
 wyslane = wyslij_wiadomosc(
     e_mail_odbiorcy, temat, wiadomosc,
)
 ```

 Deklaracja zmiennych takich jak lista, tablica, krotka czy słownik dzięki wcięciom często poprawia ich czytelność co jest główną zasadą, która kierowano się określając reguły formatowania kodu w Pythonie.

 ```python
 lista = [
     1, 2, 3,
     4, 5, 6,
 ]
 ```

 W przypadku łamania linii i operatorów np.. arytmetycznych obowiązuje zasada przenoszenia operatora do nowej linii.

```python
 zysk = (
     przychod
     - koszty
     - podatki
 )
 ```

 ### Puste linie

 Funkcje najwyższego rzędu oraz definicje klas oddzielamy od pozostałych bloków kodu dwiema pustymi liniami.

 ```python
 def zrob_cos():
    return 'zrobione'


def tez_cos_zrob():
    return 'też zrobione'
 ```

 Metody klas oraz funkcje lokalne oddzielone są natomiast pojedynczą pustą linią.

 ```python
 class Osoba:
    def __init__(self, imie, nazwisko, plec):
        self.imie = imie
        self.nazwisko = nazwisko
        self.plec = plec
        
    def przedstaw_sie(self):
        print(f'Nazywam się {self.imie} {self.nazwisko}')

    def moja_plec(self):
        print(f'Moja płeć to {self.plec}')
        

os = Osoba('Krzysztof', 'Ropiak', 'mężczyzna')
os.przedstaw_sie()
os.moja_plec()
 ```

Pojedyncze puste linie mogą być również stosowane wewnątrz funkcji aby odseparować od siebie logiczne sekcje funkcji.

 ```python
 def funkcja_top_level():
    
    def funkcja_lokalna():
        pass
    
    def kolejna_funkcja_lokalna():
        pass
 ```

 ### Import modułów

 Poszczególne instrukcje importu powinny być rozdzielone na oddzielne linie.

 ```python
 # Tak poprawnie importujemy moduły:
 import os
 import sys

 # Tak nie robimy:
 import os, sys
 ```

 Poprawny jest natomiast taki sposób definiowania importu:

 ```python
 from subprocess import Popen, PIPE
 ```

W momencie gdy importów z jednego modułu jest dużo warto zastąpić to w ten sposób:

```python
from rest_framework.mixins import (
    ListModelMixin,
    CreateModelMixin,
    RetrieveModelMixin,
)
```

Importy  powinny  być  umieszczane  na  początku  pliku  tuż  za  ewentualnymi  komentarzami  dla  modułu  i elementami docstring. Kolejnośc importów ma również znaczenie. Oto zalecany porządek:

- import bibliotek standardowych
- import powiązanych bibliotek zewnętrznych (ang. third party imports)
- import lokalnych aplikacji/bibliotek

Zalecane jest również dodawanie pustej linii po każdej z w/w grup importów. Jako, że Python umożliwia zarówno import całej biblioteki lub tylko wybranych jej modułów często trzeba dobrać odpowiedni sposób do sytuacji,  ale  z  reguły  zaleca  się  wykonywanie  importu  i  dodanie  aliasu  lub  import  modułu  zamiast  np. konkretnej klasy z tego modułu co zmniejsza ryzyko wystąpienia konfliktów w przestrzeninazw. Więcej informacji oraz przykłady znajdują się w rozdziale poświęconym zarządzaniu i importowi pakietów.

### Inne zalecenia

Zmienne typu string można umieszczać zarówno w cudzysłowie lub w apostrofach, gdyż w przypadku Pythona nie ma to znaczenia. Natomiast PEP8 nie zaleca żonglowania tym zapisem i trzymania się jednej z opcji. Sytuacją, w której dozwolone jest użycie obu jednocześnie jest ciąg tekstowy, który sam już zawiera cudzysłów lub apostrof – tedy należy użyć drugiego z nich. Każdy z następujących wpisów jest poprawny:

```python
artykul = 'Recenzja "Władcy Pierścieni".'
artykul = "Recenzja \"Władcy Pierścieni\"."
artykul = """Recenzja "Władcy Pierścieni"."""
```

Spacje w wyrażeniach i definicjach są pożądane, ale nie należy ich nadużywać.

```python
# Dobry zapis:
zakupy(szynka[1], {jajka: 2})
x = 1
lista[index]
lista[1:4]

# Tak nie robimy:
zakupy( szynka[ 1 ], { jajka: 2 } )
x=1
lista [index]
lista[1: 4]
```

Wszystkie operatory binarne powinny być otoczone pojedynczą spacją.

## Podstawowe typy danych

Zanim przejdziemy do omawiania poszczególnych typów danych warto wiedzieć, że Python jest językiem „typowanym dynamicznie”. Oznacza to, że typ danych jaki zostanie wykorzystany do przechowania wartości przypisanej do zmiennej często zależy od wartości jaka zostanie do zmiennej przypisana co znacznie różni się od sposobu w jaki typy są przypisywane do zmiennych w Javie czy C++.

Takie rozwiązanie ma zarówno wady jak i zalety. Do wad można zaliczyć to, że pierwotny typ zmiennej może ulec zmianie w dalszej części kodu co wymusza na programiście większą kontrolę tego co dzieje się z tą zmienną i czasami trzeba stosować funkcje, które sprawdzają typ przekazanych danych. Nie możemy też w żaden sposób wymusić przekazania do metody danych określonego typu lub określić jaki typ danych zostanie zwrócony. Zaletą dynamicznego typowania jest większa elastyczność języka i możliwość zmiany typu w locie co eliminuje konieczność jawnego deklarowania nowych zmiennych do przechowywania danych pod postacią innego typu (rzutowanie jawne i niejawne).

Kolejna istotna informacja jest taka, że Python jest językiem zorientowanym obiektowo i wszystko w Pythonie jest obiektem`*` o czym świadczy chociażby to, że właściwie wszystkie zmienne posiadają metody, które można na nich wykonać.

> `*` - to stwierdzenie może nie być prawdą, jeżeli porównać definicje obiektu w innych językach programowania, ale z punktu widzenia Pythona i jego twórców jest prawdą.

### Kilka słów o operatorach

Zanim omówione zostaną typy danych warto poznać kilka operatorów, które w powiązaniu ze zmiennymi są często używane.

```python
# operatory arytmetyczne
suma = 1 + 2 * 3 / 4.0

# modulo czyli reszta z dzielenia
reszta = 12 % 5
kwadrat = 5 ** 2
szescian = 5 ** 3

# operacje na napisach
full_name = "Krzysztof" + " " + "Ropiak"

# ale to ?
spam = "SPAM " * 10
print(spam)

# listy
oceny = [1, 2, 3, 4, 5] * 10
print(oceny)

# operatory porównania
liczba1 = 1
liczba2 = 2
print(liczba1 > liczba2)
print(liczba1 <= liczba2)
print(liczba1 == liczba2)
print(liczba1 != liczba2)

# powyższe porównania zwrócą wartości logiczne czyli True lub False
# na wartościach logicznych możemy również wykonywac operacje
prawda = True
falsz = False
print(prawda and falsz)
print(prawda or falsz)
print(not prawda)
print(not not prawda)
print(bool(prawda or falsz))
```

Python w bardziej złożonych wyrażeniach wykonuje działania w określonej kolejności:

- najpierw `**`
- następnie `*`, `/` oraz `%`
- a dopiero na końcu `+` i `-`

W Pythonie jako fałsz traktowane są:
- liczba zero (0, 0.0, 0j itp.)
- False
- None (null)
- puste kolekcje ([], (), {}, set() itp.)
- puste napisy
- Obiekty posiadające metodę `__bool__()`, jeśli zwraca ona False

### Typy liczbowe

Dwa główne typy liczbowe Pythona to liczba całkowita oraz rzeczywiste czyli integer i float. Jest jeszcze typ complex, który służy do przechowywania wartości liczb zespolonych, ale zapoznanie się z informacjami na jego temat pozostawiam czytelnikowi.

```python
całkowita = 5
rzeczywista = 5.6

# przykład rzutowania
rzeczywista = float(56)

# poniżej kolejny przykład
liczba_str = "123"
liczba = int(liczba_str)
print(type(liczba))

# zmienne można również zadeklarować w jednej linii
a, b = 3, 4
```

W przypadku liczb rzeczywistych można również określić precyzję z jaką zostaną wyświetlone, ale stosowny przykład znajduje się w kolejnym podrozdziale.

### Typ tekstowy

We fragmentach kodu w poprzednich rozdziałach znalazło się już kilka przykładów deklaracji zmiennej typu string. Dla przypomnienia:

```python
artykul = """Recenzja "Władcy Pierścieni"."""
imie = 'Krzysztof'
hobby = "piłka nożna"
```

Ciąg tekstowy w Pythonie to tablica znaków co daje z miejsca wiele możliwości manipulacji i dostępu do składowych tego ciągu. Inna ważna cecha stringów to fakt, że po ich zadeklarowaniu nie możemy zmienić zadeklarowanych znaków ciągu. Oczywiście możemy nadpisać zmienną nową wartością lub dokleić do niej kolejny ciąg tekstowy, ale pierwotny fragment jest niezmienny. Poniżej kilka przykładów.

```python
imie = "Krzysztof"
nazwisko = "Ropiak"

# string to tablica znaków więc możemy odwołać się do jej elementów
print(imie[0])

# indeks elementu możemy również określać jako pozycja od końca ciągu
print(imie[-1])

# można również pobrać fragment ciągu (slice) określając jako indeks
# element początkowy i końcowy. Zwróć uwagę na wartość tych indeksów.
print(imie[0] + imie[-2] + imie[4:6])

# można również określic tylko jeden z dwóch indeksów
print(imie + nazwisko[3:])

# inny sposób złączania ciągów
print(imie + " " + nazwisko)

# Elementów ciągu nie można zmieniać więc poniższa instrukcja zwróci błąd.
# nazwisko[0] = "P"
# Potwierdzeniem tego, że ciąg tekstowy jej również obiektem jest możliwość
# wykonania na nim metod dla tego typu zdefiniowanych. Metoda count() zlicza
# ilość wystąpień danego ciągu w wartości przechowywanej przez zmienną.
print(imie.count("z"))

# Co ciekawe w Pythonie możemy wywoływać funkcje dla danego obiektu już podczas deklaracji
# co na pierwszy rzut oka może wyglądać dość egzotycznie.
print("Jesteś szalona!".count("a"))

# Potwierdzeniem niezmienności zadeklarowanego stringa może być również poniższy kod
print(imie.lower())
print(imie)

# Aby zwrócić długość ciągu tekstowego należy posłużyć się wbudowaną funkcją len()
print(len(nazwisko))
```

Ciągi tekstowe bardzo często są „dekorowane” innymi wartościami przed ich wydrukowaniem na konsolę. Ciąg wyjściowy może być zlepkiem innych ciągów i/lub liczb, ale nie możemy tak po prostu wykonać poniższej operacji:

```python
print("Ala ma " + 4 + " lata")
```

Interpreter Pythona zwróci błąd z informacją, że nie może wykonać niejawnej konwersji z typu int na typ string. Poniżej listing z możliwościami jakie mamy do dyspozycji.

```python
# formatowanie znane z Pythona 2.x
wyznanie = "Lubię %s" % "Pythona"
print(wyznanie)
wonsz = "Python"
print("Lubię %sa" % wonsz)
print("Lubię %s oraz %sa" % ("Pythona", wonsz))

# %s oznacza, że w miejsce tego znacznika będzie podstawiany ciąg tekstowy
# %i - to liczba całkowita
# %f - liczba rzeczywista lub inaczej zmiennoprzecinkowa
# %x lub #X - liczba całkowita zapisana w formie szesnastkowej
print("Używamy wersji Python %i" % 3)
print("A dokładniej Python %f" % 3.5)
print("Chociaż lepiej to zapisać jako Python %.1f" % 3.5)
print("A kolejną glówną wersją Pythona może być wersja %.4f" % 3.6666)
print("A może będzie to wersja %.1f ?" % 3.6666)
print("A może jednak %.f ?" % 3.6666)
wersja = 4
print("A %i w systemie szesnastkowym to %X" % (wersja, wersja))
print("A %i * %i szesnastkowo daje %X" % (wersja, wersja, wersja*wersja))

# Chociaż możliwości przy korzystaniu z mechanizmów powyżej są spore,
# to i kilka wad się również znajdzie. Trzeba pilnować zarówno liczby argumentów jak
# i ich kolejności. Konieczne jest powielanie tej samej zmiennej jeżeli kilka
# razy jest wykorzystywana w formatowanym ciągu. Spójrzmy na inne możliwości.
print("Lubię %(jezyk)s" % {"jezyk": "Pythona"})
print("Lubię %(jezyk)s a czy Ty lubisz %(jezyk)s ?" % {"jezyk": "Pythona"})

# wadą jest dość duża ilość dodatkowego kodu do napisania, ale nazwy zmiennych
# w ciągu pozwalają na ich szybką identyfikację i wielokrotne wykorzystanie w
# dowolnej kolejności
# poniżej kolejny sposób
print("Lubię język {1} oraz {0}".format("Java", "Python"))

# w nowej wersji języka Python możliwe jest również odwoływanie się do elementów kolekcji
# lub pól klasy
class Osoba:
    def __init__(self, imie, nazwisko):
        self.imie = imie
        self.nazwisko = nazwisko
kr = Osoba("Krzysztof", "Ropiak")
print("Tą osobą jest {0.imie} {0.nazwisko}".format(kr))

## Lub mój ulubiony sposób (Łukasz) w następujący sposób:
print(f'Tą osobą jest {kr.imie} {kr.nazwisko}')
```

Mimo, iż ilość przykładów i sposobów tutaj przedstawionych jest dość duża i wyczerpuje większość najczęstszych przypadków to w dokumentacji można znaleźć jeszcze wiele dodatkowych możliwości. Po więcej przykładów można udać się pod poniższe adresy:

1. https://docs.python.org/3/library/string.html#format-string-syntax
2. https://pyformat.info/

## Listy

Lista w języku Python to kolekcja, którą można porównać do tablic w innych językach programowania. Ważną cechą list jest to, że mogą przechowywać różne typy danych. Rozmiar tablicy ograniczony jest możliwościami sprzętu. Listę możemy zainicjalizować w poniższy sposób:

```python
lista = []
lista2 = list()
lista3 = [1, 2, 3]
lista4 = ["a", 5, "Python", 7.8]
```

Do elementów listy odwołujemy się tak samo jak do elementów ciągu tekstowego gdyż tam również mamy do czynienia z listą (chociaż są to obiekty typu string).

Możemy również umieszczać listy w liście, co daje nam listy wielopoziomowe.

```python
lista5 = [lista3, lista4]
```

Po wypisaniu takiej listy otrzymamy:

```python
 [[1, 2, 3], ['a', 5, 'Python', 7.8]]
```

W Pythonie można też w łatwy sposób łączyć ze sobą listy:

```python
lista3.extend(lista4)
print(lista3)
wyjście -> [1, 2, 3, 'a', 5, 'Python', 7.8]

# lub w prostszy sposób
lista6 = lista3 + lista4
print(lista6)
Wyjście -> [1, 2, 3, 'a', 5, 'Python', 7.8]
```

Obie metody różnią się od siebie tym, że pierwsza modyfikuje już istniejącą listę, a druga wymaga podstawienia połączonej listy pod zmienną gdyż sama arytmetyczna operacja `+` nie spowoduje zmiany pierwotnej listy.

Niektóre metody, które można wykonać na obiekcie listy wykonują się jako operacje in-place co oznacza, że operacja wykonywana jest bez zwracania nowej wartości przez co nie można zmienionej tablicy przypisać do innej zmiennej. Poniżej przykład z sortowaniem:

```python
lista7 = [7, 9, 3, 1]
posortowana = lista7.sort()
print(lista7)
print(posortowana)

# wyjście
[1, 3, 7, 9]
None
```

Wartość `None` w Pythonie odpowiada wartości Null w innych językach programowania. Nie możemy też posortować tablicy, w której znajdują się liczby oraz ciągi tekstowe.

Listy mogą być „cięte” (ang. sliced) tak jak ciągi tekstowe przedstawione w poprzednim rozdziale.

Dodawanie, usuwanie i zmiana wartości elementów listy może być wykonywana na wiele sposobów. Poniżej listing z niektórymi z nich.

```python
# wstawianie i usuwanie elementów listy
skala = [1, 2, 3, 4, 5]

# dodajemy element na końcu listy
skala.append(6)
print(skala)

# znamy już sposób odwoływania się do elementu listy poprzez indeks więc można
# wartości listy ustawiać w ten sposób, ale nie da się wstawić wartośći na
# indeksie, który nie istnieje
skala[6] = 7

# zostanie zwrócony błąd IndexError: list assignment index out of range
# ale można zrobić to np. tak
skala[6:] = [7]

# lub tak
skala[len(skala):] = [7]

# alternatywnym sposobem jest wywołanie metody insert
skala.insert(6, 7)
print(skala)

# usuwamy element z końca listy co powoduje, że z wykorzystaniem
# tych metod osiągamy funkcję stosu
skala.pop()
print(skala)

# pop może również przyjmować indeks elementu do usunięcia.
# Metoda pop zwraca również wartość elementu usuwanego
skala.pop(2)
print(skala)
```

Do usuwania elementów listy można wykorzystać również wbudowaną funkcję del(), która nie zwraca żadnej wartości. Za jej pomocą można również usuwać zmienne.

W tym rozdziale zostały zaprezentowane podstawy jeżeli chodzi o operacje na listach. Python oferuje wiele bardziej rozbudowanych możliwości generowania, wybierania, sortowania list jednak najpierw muszą zostać wprowadzone takie pojęcia jak pętla czy instrukcja warunkowa. W dokumentacji można również znaleźć przykłady korzystające z instrukcji lambda, ale jej użycie będzie omawiane szerzej podczas zajęć z zaawansowanego Pythona.

### Krotki

Krotki (ang. tuples) są bardzo podobne do list z tą różnicą, że są typem niezmiennym i deklaracja zmiennych zapisywana jest w nawiasach zwykłych a nie kwadratowych. Również mogą przechowywać wiele typów danych jednocześnie.

```python
# tworzymy krotke
krotka = (1, 2, "Jacek", "ma")
krotka_liczb = krotka[:2]
print(krotka_liczb)
krotka_stringow = krotka[2:]
print(krotka_stringow)
nowa_krotka = tuple()
najnowsza_krotka = tuple([1, 2, 3])

# możemy również rzutować typy krotka - lista
lista = [1, 2, "Ala", "też", "ma"]
krotka_z_listy = tuple(lista)
nowa_lista = list(krotka_z_listy)

# krotki mogą być zagnieżdżane
duza_krotka = krotka_stringow, krotka_liczb, tuple(nowa_lista) print(duza_krotka)

# a jeżeli zagnieździmy listę w krotce ?
listokrotka = krotka_z_listy, lista

# to nadal możemy modyfikować elementy listy
listokrotka[1][0] = 0
print(listokrotka)

# pakowanie krotki (tuple packing)
t = 5, 6, 7
print(t)
x, y, z = t

# i rozpakowywanie krotki (tuple unpacking)
# inny sposób łączenia zmiennych różnego typu w string print("x = " + str(x))
print("y = " + repr(y))
print("z = " + str(z))

# na wyjściu
(1, 2)
('Jacek', 'ma')
(('Jacek', 'ma'), (1, 2), (1, 2, 'Ala', 'też', 'ma'))
((1, 2, 'Ala', 'też', 'ma'), [0, 2, 'Ala', 'też', 'ma'])
(5, 6, 7)
x=5
y=6
z=7
```

### Słowniki

Słowniki to tablica mieszająca lub inaczej tablica z haszowaniem, którą można porównać do tablic asocjacyjnych znanych z innych języków programowania. Słowniki przechowują pary klucz:wartość i właśnie po kluczu odbywa się wyszukiwanie. Kluczem w słowniku może być każdy niezmienny typ danych np., string lub liczba. Kluczem może być również krotka, jeżeli zawiera typy niezmienne (string, liczba, krotka). Klucze w słowniku są unikalne a pary elementów nie są uporządkowane w kolejności, w której zostały dodane. Słownik został już wykorzystany we wcześniejszych przykładach w podrozdziale z formatowaniem ciągów tekstowych.

Poniżej fragmenty kodu tworzące słownik oraz pokazujące jak uzyskać dostęp do jego danych.

```python
# tworzenie słownika
slownik = {}
slownik = dict([("jeden", 1), ("dwa", 2), ("trzy", 3)]) slownik = dict(jeden=1, dwa=2, trzy=3)
slownik = dict({"jeden": 1, "dwa": 2, "trzy": 3}) slownik = {"jeden": 1, "dwa": 2, "trzy": 3}
print(slownik["jeden"])

# sprawdzenie czy klucz jest w słowniku czy nie
print("jeden" in slownik)

# wypisanie wszystkich kluczy
print(slownik.keys())

# wypisanie wszystkich wartości
print(slownik.values())

# można również sprawdzić czy klucz występuje w słowniku # w przedstawiony poniżej sposób, ale jest on wolniejszy print("jeden" in slownik.keys())
# dodanie elementu do słownika
slownik["cztery"] = 4
print(slownik.keys())
```

### Zbiory

Zbiór (ang. set) to nieuporządkowana kolekcja, której ważną cechą jest to, że znajdują się w niej unikalne elementy (czyli bez powtórzeń). Zbiory obsługują również matematyczne operacje, które z teorii zbiorów są znane: suma, przecięcie, różnica oraz różnica symetryczna.

```python
# inicjalizacja zbiorów
klasa = {"Marek", "Janek", "Ania", "Ewa", "Marek", "Ania"} print(klasa) # duplikatów już nie ma

# a teraz zbiór znaków ze stringa
czar = set("czabunagunga")
print(czar)
inny_czar = set("abrakadabra")
print(inny_czar)
print(czar - inny_czar) # są w czar, ale nie ma w inny_czar
print(czar.difference(inny_czar)) # to samo, ale inaczej
print(inny_czar - czar) # to nie to samo, jak wiadomo z teorii
print(czar | inny_czar) # znaki w czar lub inny_czar lub obu
print(czar & inny_czar) # przecięcie czyli część wspólna 
print(czar.intersection(inny_czar)) # można tak
print(czar ^ inny_czar) # różnica symetryczna
```

Bardzo przydatna staje się własność unikalnych elementów zbioru jeżeli chcemy wyeliminować duplikaty z listy, gdyż wystarczy rzutować listę na zbiór i sprawa załatwiona a następnie, jeżeli na wyjściu potrzebujemy znowu listy to rzutujemy w odwrotną stronę.

### Funkcja range

Funkcja (chociaż nazywając precyzyjniej to niezmienna sekwencja) range służy to generowania ciągu liczb według zadanych parametrów. Często przydaje się w pętlach lub podczas tworzenia list lub zbiorów liczb. Funkcja range() i sposób jej użycia zmieniał się w trakcie rozwoju języka i jej zastosowanie w wersji Python 2.x różni się od tego co będzie zaprezentowane tutaj. Zapoznanie się ze szczegółami pozostawiam czytelnikowi.

Poniższe fragmenty kodu zaprezentują sposób działania funkcji range.

```python
from decimal import *

# jakim typem jest range ?
liczby = range(5)
print(type(liczby)) # range jest obiektem typu range (w Python 2.x była to lista)

# range może przyjmować 1 parametr, wtedy jest to parametr stop
for i in range(10):
    print(i)

# range może też przyjmować 2 parametry (start, stop)
for i in range(4, 10):
    print(i)

# lub 3 parametry (start, stop, step)
for i in range(4, 10, 2):
    print(i)

# możemy również generować wartości ujemne
for i in range(-5, -1):
    print(i)
for i in range(-5, -10, -2):
    print(i)

# lista z elementów funkcji range
lista = list(range(10))
print(lista)

# funkcja range nie generuje wartości zmiennoprzecinkowych, ale można
# dość łatwo taką funkcję stworzyć
def frange(start, stop, step):
    i = start
    while i < stop:
        yield i
        i += step
for i in frange(0.1, 0.5, 0.1):
    print(i)

# po wyświetleniu wyniku można się zdziwić bo 0.3 to właściwie nie 0.3...
# to może jeszcze raz, ale tak
for i in frange(0.1, 0.5, 0.1):
    print(Decimal(i))
print((0.1 + 0.2) == 0.3)  # kto by się spodziewał ?
print(round((0.1 + 0.2), 2) == round(0.3, 2))  # teraz lepiej
print((Decimal(0.1) + Decimal(0.2)) == Decimal(0.3))
print((Decimal('0.1') + Decimal('0.2')) == Decimal('0.3'))
```

Dla zainteresowanych problemem reprezentacji liczb zmiennoprzecinkowych w systemie dwójkowym odsyłam do dość zrozumiale napisanego artykułu http://www.samouczekprogramisty.pl/liczby-zmiennoprzecinkowe/

# Ćwiczenia

Zasad, które opisane są w dokumencie PEP8 jest więcej, ale nie wszystkie będą tutaj przytoczone. Poświęć ok. 15 minut na zapoznanie się z dokumentem PEP8 (link na początku rozdziału) i przejrzyj pokazane tam  przykładowe  fragmenty  kodu.  Zwróć  uwagę  na  informacje  w  sekcji  „Comments”  oraz  „Naming Conventions”.

Na sam koniec warto dodać, że edytor środowiska PyCharm posiada zaimplementowany mechanizm formatowania kodu wg. PEP8 więc nawet jak złamiemy zasadę wcięć, odstępów lub inną, zostaniemy o tym fakcie  poinformowanico umożliwi dokonanie poprawek  lub  skorzystanie  z  automatycznego  formatowania. Czasem jednak automatyczne formatowanie potrafi się pogubić...

1. Pobierz ze strony https://pl.lipsum.com/ tekst akapitu o tytule „Czym jest Lorem Ipsum” i przypisz go do zmiennej.
2. Wyświetl na konsoli tekst postaci "W tekście jest {liczba_liter1} liter ... oraz {liczba_liter2} liter ...” . W miejsca { } podstaw zmienne, które będą przechowywały liczbę wystąpień danych liter. Litery, które mają być wyszukane powinny zostać przekazane jako indeks do 3 znaku nazwiska oraz 2 znaku imienia osoby wykonującej ćwiczenie, np. imie = „Krzysztof”, nazwisko = „Ropiak”, litera_1 = imie[2], litera_2 = nazwisko[3].
3. Przejdź na stronę https://pyformat.info/ a następnie zapisz w oddzielnym pliku .py i wykonaj 5 wybranych przykładów formatowania ciągów oznaczonego jako „New”, których nie było w przykładach z tego podrozdziału (np. z wyrównaniem, ilością pozycji liczby, znakiem itp.).
4. Mając dany poniższy fragment kodu (kod umieść w pliku):
   ```python
   print(dir(zmienna_typu_string))
   help(zmienna_typu_string.wybrana_funkcja)
   ```
   Pod zmienna_typu_string podstaw dowolny ciąg tekstowy – może być jako odwołanie do zmiennej lub bezpośrednio ciąg tekstowy. Następnie z listy metod, które wyświetli pierwsze polecenie wybierz jedną z funkcji, która nie była omawiana w podrozdziale (wybierz z tych, które w nazwie nie posiadają __ na początku i końcu) i podstaw pod tekst wybrana_funkcja w drugim wyrażeniu. Uruchom ten fragment kodu. Pojawi się opis działania wybranej funkcji. Teraz przytrzymaj klawisz CTRL i najedź kursorem myszy na nazwę wybranej funkcji w kodzie i wciśnij lewy klawisz myszy. W ten sposób można szybko przenieść się do pliku źródłowego z definicją funkcji i jej krótkim opisem.
5. Wyszukaj w Internecie pojęcie „extended slice” w kontekście Pythona i wyświetl swoje imię i nazwisko z odwróconą kolejnością znaków z kapitalikami. Np. Fotzsyzrk Kaipor
6. Stwórz listę z wartościami od 1 do 10. Następnie podziel listę tak, aby pierwsze 5 liczb zostało w oryginalnej liście a pozostałe 5 znalazło się w nowej liście.
7. Połącz te listy ponownie. Dodaj do listy wartość „0” na początku. Utwórz kopię połączonej listy i wyświetl listę posortowaną malejąco.
8. Za pomocą krotek stwórz listę studentów swojej grupy przypisując `numer indeksu` do `imienia i nazwiska` (dane nie muszą być prawdziwe).
9. Przekształć poprzednie zadanie na słownik, a następnie dodaj pary zawierające wiek, adres email, rok urodzenia oraz adres.
10. Stwórz listę zawierającą numery telefonów z powtórzeniami, a następnie usuń powtórzenia za pomocą rzutowania na `set`.
11. Korzystając z funkcji `range` wypisz elementy rosnąco od 1 - 10
12. Korzystając z funkcji `range` wypisz elementy malejąco od 100 - 20, co 5 wartości.
13. Połącz całą wiedzę wydobytą z zajęć (i zadań) i stwórz program wypisujący dane z listy, która zawiera kilka słowników (dane wypisz w postaci jednego string'a odpowiednio go formatując).
