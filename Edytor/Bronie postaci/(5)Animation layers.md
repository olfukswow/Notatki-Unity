Layersy służą do tego by np. ustawiać animacje zależnie od broni
W animatorze w pasku po lewej dodaj nowy layer i w zależności od broni nazwij go np. shotgun weapon layer następnie na środku do grafa przeciągnij plik z animacją shotgun fire i shotgun idle 

Ustaw animację idle na default(klikając PPM na blok)
Ustaw transition z any state do fire(klikając PPM na any state i wybierając "make transition") i do tego transition dodaj condition Fire

Dla obu ustaw transition duration na 0

Z fire ustaw transition do idle i ustaw exit time na 1 a transition duration 0

Ustaw layerowi odpowiedni avatar mask, czyli zapewne ten dozwalający elementy poza nogami

zmiana layeru animacji w kodzie:
(W weaponvisualcontroller.cs)
``private Animator animator;``
(w funkcji start)
``animator = GetComponentInParent<Animator>();``

(Funkcja do zmiany wagi layera)
```
 private void SwitchAnimationLayer(int layerIndex)
{
           for (int i = 0; i < animator.layerCount; i++)
    {
            animator.SetLayerWeight(i, 0);
    }
           animator.SetLayerWeight(layerIndex, 1);
}
```
Po tym wywołuj przy zmianie broni funkcją SwitchOn() też tą funkcję z indeksem odpowiednim do broni ustawianej

[[]]