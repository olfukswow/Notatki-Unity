

### Tworzenie nowej instancji obiektu
`` GameObject bullet = Instantiate(bulletPrefab, gunPoint.position, gunPoint.rotation)`` Pierwszy argument to zmienna typu GameObject zawierająca referencje do obiektu/prefabu który chcemy stworzyć, drugi argument to pozycja obiektu a trzeci to jego rotacja
### Usuwanie obiektu
``Destroy(bulletreference, 5)``
Drugi argument jest opcjonalny i oznacza czas w sekundach po jakim obiekt ma być usunięty
### Wypisywanie do konsoli
``Debug.Log("Tekst")``
### Obracanie obiektu w kierunku innego obiektu
``obiekt.LookAt(aimLocation);`` (obiekt to obiekt typu Transform)
