W packet manager zainstaluj z unity registry paczkę "animation rigging"

Następnie w liście obiektów po lewej naciśnij na główny obiekt postaci(character_main) a następnie w pasku u góry okna Animation Rigging > Rig setup

Powstał nowy children postaci, mianowicie Rig 1, PPM na Rig 1 > Create Empty, nazwij Head_aim i dla niego stwórz childrena o nazwie target

Dla Head_aim dodaj komponent Multi-Aim Constraint
###### (Multi-Aim Constraint umożliwia nakierowanie danej kości postaci na cel)

W Multi-Aim Constraint ustaw wartość constrained object na referencję do kości głowy postaci a wartość source object na chwilę temu stworzony objekt "target" 
(Sprawdź też w Multi-Aim Constraint wartości aim axis i up axis czy są dobrze ustawione naciskając na obiekt kości i sprawdzanie ktora oś obiektu musi być zmieniona by obracać głową w poziomie i która oś by unosić głowę(up axis))
![[Pasted image 20251129084548.png]]
###### Aby uzyskać widok kości postaci po prawej jak na zdjęciu w górnym pasku Animation Rigging > Bone Renderer Setup
### Teraz głowa postaci będzie podążać za obiektem target co było naszym celem, jeśli chcesz by broń też podążała za targetem to dla Rig 1 utwórz kolejnego childa o nazwie Gun_aim i wykonaj te same kroki 