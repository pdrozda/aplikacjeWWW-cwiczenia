# Modele Django

Każdy ze studentów posiada stworzoną bazę MySQL na serwerze 213.184.8.36. 
Można również zainstalować XAMPP, bądź inny serwer zawierający dostęp do bazy niekoniecznie MySQL i korzystać z bazy lokalnej.

Przykładowy użytkownik wygląda następująco:

| Dane studenta | Paweł Drozda |
| :-- | :-- |
| Login | drozdap |
| Hasło | pawel123#@!A |

Po zalogowaniu się do MySQL przez przez putty (login i hasło takie samo, jak do MySQL) można (i powinno się!) hasło zmienić.

W shellu można użyć passwd.

Dla MySQL można użyć polecenia SQL:
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

1. Zainstaluj pakiety `django` i `djangorestframework`,
2. Stwórz projekt Django,
3. Stwórz aplikację Django w projekcie z nazwą oddającą cel projektu,
4. Stwórz w aplikacji defaultowy widok (dowolny),
5. W aplikacji stwórz plik `urls.py`, który będzie wyświetlał defaultowy widok
6. W głównym pliku `urls.py` dodaj odwołanie do pliku urls w aplikacji (jako link ustaw nazwę aplikacji),
7. Przygotuj plik `models.py`, tak aby odzwierciedlał stworzony model w MySQL Workbench na poprzednich zajęciach,
8. Podepnij się pod bazę MySQL,
9. Stwórz migrację,
10. Zmigruj bazę na serwer MySQL.