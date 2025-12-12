W layerze animacji broni przeciągnij plik .fbx z animacją przeładowania i nazwij ten state np. "Weapon Reload"

W parametrach dodaj parametr typu trigger o nazwie "Reload"

Dodaj transition z any state do Weapon Reload(z condition Reload) oraz z Weapon Reload do Weapon Idle

W metodzie Update skryptu WeaponVisualController.cs
```
if(Input.GetKeyDown(KeyCode.R))
{
    animator.SetTrigger("Reload");
}
```

``private Rig rig;``
(``using UnityEngine.Animations.Rigging;``)
W starcie:
``rig = GetComponentInChildren<Rig>();``


```
        if(Input.GetKeyDown(KeyCode.R))
        {
            animator.SetTrigger("Reload");
            rig.weight = 0;
        }
```

Trzeba rigowi ustawić wagę na 0(jeśli ręka podczas animacji przeładowania zbyt oddala się to możesz ustawić tu wagę nie na 0 lecz np 0.15f)ponieważ wcześniej dodaliśmy m.in. funkcjonalność przyklejenia lewej ręki do broni czy śledzenia broni za celem przez co animacja przeładowania z wagą 1 nie zadziała gdyż właśnie owe funkcjonalności zablokują ruch ręki


### Aby po animacji z powrotem ustawić wartość riga na 1
Pod podanym wyżej ifem:
```
if(rigShouldBeIncreased)
{
    rig.weight += rigIncreaseStep * Time.deltaTime; 
    // git wartosc stepa to 2.75f
    
    if (rig.weight >= 1)
    {
        rig.weight = 1;
        rigShouldBeIncreased = false;
    }
}
```
waga jest zwiększana stopniowo gdyż natychmiastowe zwiększenie jej do 1 teleportowałaby rękę do broni

``public void ReturnRigWeightToOne() => rigShouldBeIncreased = true;``

#### ustawianie rigShouldBeIncreased na true po końcu animacji

Stwórz skrypt PlayerAnimationEvents.cs i dodaj go jako komponent obiektu postaci (Character_main)

Kod skryptu:
```
    private WeaponVisualController weaponVisualController;
    private void Start()
    {
        weaponVisualController = GetComponentInParent<WeaponVisualController>();
    }

    public void ReloadIsOver() => weaponVisualController.ReturnRigWeightToOne();

```

W pliku animacji naciśnij strzałkę na nim(by rozwinąć pliki w nim) na pliku typu motion(ikonka trójkąta w ruchu) użyj ctrl + D i nazwij te motion np. "Rifle - Reload(Editable)" i ustaw jako motion w layerze animacji w state przeładowywania

W dolnym pasku editora(tam gdzie masz eksplorator plików itp.) wybierz tab "Animation" i po lewej wybierz w menu rozwijanym animacje przed chwilą utworzoną

Na pasku całej animacji przejdź do ostatniej klatki, albo lepiej wcześniej by ręka zaczęła wracać do broni już przed końcem animacji i wybierz funkcję Add Event
![[Pasted image 20251208185927.png]]
![[Pasted image 20251208190002.png]]
i w evencie wybierz odpowiednią klasę a następnie metodę z tej klasy(W tym przypadku ReloadIsOver())
![[Pasted image 20251208190052.png]]