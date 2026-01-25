## Discrete(Typ głównie dla obiektów poruszających się wolno w świecie gry takich jak np. propy), **Najwydajniejszy**
### Ten typ sprawdzania kolizji sprawdza kolizję tylko na początku i końcu aktualizacji fizyki danego obiektu więc np. w przypadku pocisku gdy przeleci on przez dany obiekt to ten obiekt nie wykryje kolizji gdyż to nie na nim zakończyła się aktualizacja fizyki pocisku
## Continous dynamic (Typ głównie dla szybkich i wymagających dokładności obiektów czyli głównie pocisków), **Obiciążający wydajność**
### Ten typ sprawdzania kolizji sprawdza kolizję z dowolnym obiektem przy każdej aktualizacji fizyki

### Continous
### Działanie jest takie jak w przypadku continous dynamic lecz ten typ wykrywa wyłącznie kolizję wobec obiektów kinematic(obiekty nie reagującego na inne obiekty fizycznie lecz ruchliwa poprzez transform) oraz static(nie ruchliwe obiekty w świecie gry)