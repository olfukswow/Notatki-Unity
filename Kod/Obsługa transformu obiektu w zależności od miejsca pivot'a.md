### Czym jest pivot?
pivot to punk obiektu do którego odnosi się transform(zdjęcie pivota poniżej)
![[Pasted image 20260123162433.png]]
W przypadku obiektów z unity np. 3D Cube pivot jest w środku obiektu, natomiast w przypadku stworzonych przez kogoś może być on w środku obiektu lub na jego dole(co ułatwia ustawianie na ziemi np. propów)

```
 if (target.GetComponent<Renderer>() != null)
 {
     Vector3 targetCenter = target.GetComponent<Renderer>().bounds.center;
     }
```
(target to obiekt typu transform)

Obiekty modeli 3D stworzone w np. blenderze zawierają komponent Renderer więc sprawdzamy jego obecność - jeśli obiekt posiada renderer wyznaczamy środek poprzez Renderer
