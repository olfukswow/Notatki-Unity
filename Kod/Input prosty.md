#### ``Input.mousePosition``
##### Zwraca pozycję myszy względem obrazu widzianego przez użytkownika przez kamerę jako Vector3
#### Pozycja myszy względem warstwy
##### Kod
```
Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
RaycastHit hit;
if(Physics.Raycast(ray, out hit, Mathf.Infinity, whatIsAimMask))
{
    Debug.Log(hit.point);
}
```
###### whatIsAimMask to obiekt typu LayerMask zdefiniowany w klasie i w edytorze musi być ustawione w tej zmiennej względem jakiego layer'u będa podawane koordynaty jako Vector3

### ``Input.GetAxis("Argument")``
#### W zależności od argumentu zwraca dane o inpucie, w przypadku argumentu "Vertical" zwraca dane z przycisków W, S, strzałek góra i dół a w przypadku argumentu "Horizontal" zwracana dane z przycisków A,D, strzałek lewo i prawo. Zazwyczaj wykorzystywane by zapisać do zmiennej odpowiedzialnej za ruch wartości z klawiszy, zazwyczaj jest to robione w funkcji Update. **W przypadku funkcji ``GetAxis`` Wartości zmieniają się stopniowo np. z 0 do 1 rosną przez wartości 0.0 -> 0.3 -> 0.7 -> 1.0, natomiast gdy wartości od razu mają wynosić np. 0.0 -> 1.0 trzeba użyć funkcji o tym samym działaniu - ``GetAxisRaw``**
#### Przykład użycia
##### ``verticalInput = Input.GetAxis("Vertical");``
#### Wartości dla klawiszy
##### Vertical
###### Klawisz W i klawisz strzałki do góry - Wartość: 1
###### Klawisz S i klawisz strzałki w dół - Wartość: -1

##### Horizontal
###### Klawisz A i klawisz strzałki w lewo - Wartość: 1
###### Klawisz D i klawisz strzałki w prawo - Wartość: -1
### ``if(Input.GetKeyDown(KeyCode.R))``
Zwraca 1 gdy naciśnięty jest wybrany przycisk, jest też funkcja ``GetKey()`` która zwraca 1 gdy przycisk jest trzymany i ``GetKeyUp()`` zwracająca 1 gdy przycisk został puszczony
### ``if(Input.GetMouseButtonDown(0))``
Zwraca 1 jeśli naciśnięty został przycisk myszy lewy