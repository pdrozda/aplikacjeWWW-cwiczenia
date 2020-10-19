# Modele Django

Każdy ze studentów posiada stworzoną bazę MySQL na serwerze bad.uwm.edu.pl. Przykładowy użytkownik wygląda następująco:

| Dane studenta | Łukasz Żmudziński |
| :-- | :-- |
| Login | zmudzinskil |
| Hasło | lukasz |

Po zalogowaniu się do MySQL przez [Panel PHPMyAdmin](http://bad.uwm.edu.pl/phpmyadmin/) można (i powinno się!) hasło zmienić.

Można tego dokonać również poleceniem SQL:
```sql
# Nazwe usera podajemy zamiast user
SET PASSWORD FOR 'user'@'%'=PASSWORD('nowe_haslo');
```

i ewentualnie:

```sql
flush privileges;
```

# Ćwiczenia

Celem ćwiczenia jest stworzenie projektu w Django

1. Sprawdź czy masz włączone wirtualne środowisko – jeśli nie to włącz/stwórz,
2. Zainstaluj pakiety `django` i `djangorestframework` (UWAGA! Jeżeli wykorzystana będzie baza z serwera bad należy użyć wersji `django==2.0.13`, począwszy od wersji 2.1 Django nie obsługuje już MySQL w wersji 5.5),
3. Stwórz projekt Django,
4. Stwórz aplikację Django w projekcie z nazwą oddającą cel projektu,
5. Stwórz w aplikacji defaultowy widok (dowolny),
6. W aplikacji stwórz plik `urls.py`, który będzie wyświetlał defaultowy widok
7. W głównym pliku `urls.py` dodaj odwołanie do pliku urls w aplikacji (jako link ustaw nazwę aplikacji),
8. Przygotuj plik `models.py`, tak aby odzwierciedlał stworzony model w MySQL Workbench na poprzednich zajęciach,
9. Podepnij się pod bazę MySQL (dane do bazy dostaniesz od prowadzącego),
10. Stwórz migrację,
11. Zmigruj bazę na serwer MySQL.