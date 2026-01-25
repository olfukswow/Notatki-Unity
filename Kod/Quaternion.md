Klasa reprezentuje ruch w innej formie
Funkcja Slerp
```
 transform.rotation = Quaternion.Slerp(transform.rotation, desiredRotation, turnSpeed * Time.deltaTime); // film 38
```
Funkcja Slerp umożliwia płynny ruch z jednego punktu do drugiego - pierwszy parametr to miejsce startowe, drugi koncowe a trzeci to o ile zwiększana może być wartość