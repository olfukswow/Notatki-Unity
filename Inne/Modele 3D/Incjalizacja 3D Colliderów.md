## #1 - Najdokładniejsza opcja
Dla obiektu w świecie gry dodaj mu komponent mesh collider który odwzoruje kształt obiektu
**Problemem tego sposobu jest ogromna strata w wydajności i problem w przypadku gdy obiekt ma wykazywać ruch - unity nie zdąży obliczyć np. grawitacji dla takiego collidera**

**W przypadku gdy 2 i 3 opcja się nie sprawdzą a obiekt nie będzie się poruszał w przestrzeni możesz użyć tego sposobu i w inspektorze zaznaczyć go jako static dzięki czemu obiekt nie będzie potrzebował kalkulacji i mesh renderer nie będzie tak obciążający**
![[Pasted image 20260123112223.png]]
## #2 - Dokładna i wydajniejsza opcja
Dla obiektu w świecie gry dodaj mu komponent mesh collider który odwzoruje kształt obiektu lecz w opcjach collidera zaznaczamy opcję "convex" która uprości collider(mniej punktów collidera) np.
![[Pasted image 20260123111651.png]]
jak widać w przypadku krzesła nie jest to najlepsza opcja, lecz w przypadku prostej tekstury np. drzwi będzie to już wystarczająco skuteczne
## #3 - Pracochłonna lecz najwydajniejsza opcja
Dla obiektu w świecie gry stwórz empty child'a i pododawaj ręcznie temu childowi odpowiedne collidery które ręcznie poustawiasz tak jak chcesz