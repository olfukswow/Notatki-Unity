
## ``[RequireComponent(typeof(Rigidbody))]``
### Skrypt z tym headerem dodany do danego obiektu wymaga podanego w argumencie komponentu, jeśli obiekt go nie ma to atrybut doda ten komponent automatycznie


## ``Header``
### Dodaje nagłówek podany w argumencie w Inspectorze nad polem
### Przykład użycia:
#### ``[Header("Ustawienia gracza")]


## ``SerializeField``
### Pozwala serializować prywatne pole, by było widoczne w Inspectorze Unity
### Przykład użycia:
``[SerializeField] private float zmiennaWidocznaWInspektorze;``

## ``Space``
### Tworzy przerwę w inspektorze, może być wywołane bez argumentu tworząc jedną linię przerwy lub z argumentem gdzie argument jest typu int i oznacza ilość linii przerwy
### Przykład użycia:
``[Space(2)]`` lub ``[Space]``

## ``HideInInspector``
### Ukrywa pole w Inspectorze, mimo że jest serializowane
### Przykład użycia:
#### ``[HideInInspector]``

## ``Range``
### Dodaje suwak w Inspectorze dla wartości liczbowej
### Przykład użycia:
#### ``[Range(0,10)]``

## ``Tooltip``
### Pokazuje podpowiedź po najechaniu myszką w Inspectorze
### Przykład użycia:
#### ``[Tooltip("Dane gracza")]``
