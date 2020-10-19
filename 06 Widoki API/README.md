# Widoki API

Django REST Framework udostępnia klasę APIView, która dziedziczy po klasie `View` Django.

Klasy `APIView` różnią się od zwykłych klas `View` pod następującymi względami:
- Żądania przekazywane do serwera będą instancjami `Request`, a nie instancjami `HttpRequest` z Django.
- Metody mogą zwracać odpowiedź `Response` zamiast `HttpResponse` Django.
- Wszelkie wyjątki `APIException` zostaną wychwycone i zamieszczone w odpowiedziach.
- Przychodzące żądania zostaną uwierzytelnione, a przed wysłaniem żądania do metody obsługi uruchomione zostaną odpowiednie uprawnienia i sprawdzanie danych.

Używanie klasy `APIView` jest prawie takie samo jak używanie zwykłej klasy `View`. Jak zwykle, przychodzące żądanie jest wysyłane do odpowiedniej metody obsługi, takiej jak `.get()` lub `.post()`. Ponadto w klasie można ustawić wiele atrybutów, które kontrolują różne aspekty zasad API.

Przykład ponizej:

```python
from rest_framework.views import APIView
from rest_framework.response import Response
from rest_framework import authentication, permissions
from django.contrib.auth.models import User

class ListUsers(APIView):
    """
    View to list all users in the system.

    * Requires token authentication.
    * Only admin users are able to access this view.
    """
    authentication_classes = [authentication.TokenAuthentication]
    permission_classes = [permissions.IsAdminUser]

    def get(self, request, format=None):
        """
        Return a list of all users.
        """
        usernames = [user.username for user in User.objects.all()]
        return Response(usernames)
```

Pełna dokumentacja DRF dla widoków dostępna tutaj:

- https://www.django-rest-framework.org/api-guide/views/

## Permissions

Sprawdzanie uprawnień jest zawsze uruchamiane na samym początku widoku, zanim będzie można kontynuować dowolny inny kod. Podczas sprawdzania uprawnień zwykle wykorzystuje się informacje uwierzytelniające we właściwościach request.user i request.auth w celu ustalenia, czy przychodzące żądanie powinno być dozwolone.

Dokumentacja uprawnień:

- https://www.django-rest-framework.org/api-guide/permissions/

Przykład:

```python
from rest_framework.permissions import IsAuthenticated  # Import
from rest_framework.response import Response
from rest_framework.views import APIView

class ExampleView(APIView):
    permission_classes = [IsAuthenticated]  # Ustawianie klas zezwolen

    def get(self, request, format=None):
        content = {
            'status': 'request was permitted'
        }
        return Response(content)
```


# Ćwiczenia

Celem ćwiczeń będzie stworzenie widoków (endpointów), dzięki którym użytkownik będzie mógł łączyć się z naszym API by pobierac, edytować czy usuwać dane. W tym celu zostanie użyte `djangorestframework`.

1. Odpal swoje środowisko `virtualenv`, w którym już masz zainstalowane `django`.
2. Za pomocą `pip` doinstaluj `djangorestframework`, jeżeli jeszcze tego nie zrobiłeś,
3. Dodaj `'rest_framework'` do zainstalowanych aplikacji w swoim projekcie Django,
4. Dodaj widoki drf do `urlpatterns` swojego projektu:
   ```
   url(r'^api-auth/', include('rest_framework.urls'))
   ```
5. Stwórz widoki dla swoich modeli na podstawie [dokumentacji](https://www.django-rest-framework.org/tutorial/3-class-based-views/). A następnie dodaj je do `urlpatterns` by wyświetliły się w liście dostępnych endpointów API.
   - Zwróć uwagę, które modele powinny mieć możliwość dodawania, usuwania czy edytowania informacji. Może niektóre powinny tylko wyświetlać dane?
   - Pamiętaj by zastosować serializery z poprzednich zajęć.
6. Dodaj zezwolenia do aplikacji, tak by tylko zarejestrowani uzytkownicy mogli korzystać z endpointów,
7. Dodaj endpointy, które są dostępne tylko dla administratora.