W przypadku .fbx mającego wiele broni jako jedna paczka, plik przeciągnij go do listy obiektów i wtedy PPM na parenta tych broni > Prefab > Unpack Fully a następnie wszystkie obiekty broni wyselectuj i przeciągnij poza parenta by nie były już childami

Dla modelu broni i jego emisji zrób parenta o nazwie np. Weapon_Rifle
Dla wszystkich parentów broni zrób parenta o nazwie Weapon_Holder

Ustaw dla każdej z broni w holderze pozycje (0,0,0)

Przypisz Weapon_Holder jako child dla indeksu lewej ręki lub indeksu prawej ręki postaci(zależnie od uznania która jest lepsza do ustalania położenia broni), przykładowa ścieżka do ręki poniżej oraz przykładowe przypisanie holdera jako child indeksu prawej ręki
![[Pasted image 20251128194019.png]]
![[Pasted image 20251128194111.png]]

następnie dostosuj manulanie pozycje każdej broni do wyglądu
