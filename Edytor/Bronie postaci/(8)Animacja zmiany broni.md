(nazwa animacji na mixamo to "grab rifle from behind")

W common weapon layer PPM na wolną przestrzeń > Create State > From New Blend Tree i nazwij "Weapon Grab"
a w syncujących layerach PPM na powstały blend tree > Create new BlendTree in state

Dodaj transition z any state do Weapon Grab (PPM any state > make transition)

Dodaj w layerze parametr typu trigger o nazwie "Weapon Grab" i ustaw go jako condition do transitiona z any state do Weapon Grab

Dodaj transition z Weapon Grab do Idle(exit time 1)

Dodaj boola "BusyWeaponGrabbing"(kontroluje możliwość animacji np. strzelania podczas trwania zmiany broni) i dodaj go jako condition(zmienna musi być false) dla przejścia z any state do Fire i dla przejścia z any state do reload

### Wewnątrz Blend Tree(2x LPM na state Weapon Grab)
Dodaj parametr float "WeaponGrabType"(float ponieważ Blend Tree nie obsługuje int)

W inspektorze Blend Tree wybierz ten parametr
Poniżej dodaj motion z dostępnymi animacjami zmiany broni


W WeaponVisualController.cs
```
public enum GrabType
{
    SideGrab, BackGrab
}
```

```
private void PlayWeaponGrabAnimation(GrabType grabType)
{
    animator.SetFloat("WeaponGrabType", (float)grabType);
    animator.SetTrigger("WeaponGrab");
}
```
Ta funkcja ma być wywoływana pod każdą zmianą broni czyli np. 
##### ```
if (Input.GetKeyDown(KeyCode.Alpha1))
{
    SwitchOn(gunTransforms[0]);
    SwitchAnimationLayer(1);
    PlayWeaponGrabAnimation(GrabType.SideGrab);
}```

Aby znowu uniknąć przyklejania ręki podczas animacji trzeba chwilowo zmniejszyć wagę riga
1. Dodaj zmianę wagi riga na 0.15 (Funkcja pauseRig zawiera kod ``rig.weight = 0.15f;``)
```
 private void PlayWeaponGrabAnimation(GrabType grabType)
 {
     PauseRig();
     animator.SetFloat("WeaponGrabType", (float)grabType);
     animator.SetTrigger("WeaponGrab");
 }
```
2. W PlayerAnimationsEvents.cs
```
public void WeaponGrabIsOver() => weaponVisualController.ReturnRigWeightToOne();
```
3. Tak jak w poprzedniej notatce zduplikuj animacje (same motion) by była editable, przypisz je do Blend Tree i dodaj do tych zduplikowanych animacji event

W WeaponVisualController.cs
``[SerializeField] private TwoBoneIKConstraint leftHandIK;``
i w inspektorze przypisz do tego obiekt LeftHand_IK (Z Rig 1)
 i przy odtwarzaniu animacji przez funkcję ustawiamy jego wagę na 0
 ```
  private void PlayWeaponGrabAnimation(GrabType grabType)
 {
     leftHandIK.weight = 0f;
     
     ...
 ```
 W WeaponVisualController.cs
 ``private bool LeftHandIKShouldBeIncreased;``
 ``[SerializeField] private float leftHandIncreaseStep; //git wartosc to okolo 2.5f``
W metodzie update:
```
if(LeftHandIKShouldBeIncreased)
{
    leftHandIK.weight += leftHandIncreaseStep * Time.deltaTime;
    if (leftHandIK.weight >= 1)
    {
        leftHandIK.weight = 1;
        LeftHandIKShouldBeIncreased = false;
    }
}
```
``public void ReturnWeightToLeftHandIK() => LeftHandIKShouldBeIncreased = true;`` i dodaj wywołanie tej funkcji w funkcji WeaponGrabIsOver() w PayerAnimationsEvents.cs


### Dodanie logiki boola BusyWeaponGrabbing(dodanego do transition na początku tej notatki) tak by blokował uruchamianie innych animacji
W WeaponVisualController.cs
``private bool busyGrabbingWeapon;``

Funkcja do zarządzania wartością zmiennej
```
 public void SetBusyGrabbingWeaponTo(bool busy)
 {
     busyGrabbingWeapon = busy;
     animator.SetBool("BusyGrabbingWeapon", busyGrabbingWeapon);
 }
```
Wywołaj ją z argumentem true wewnątrz funkcji PlayWeaponGrabAnimation()
W PlayerAnimationsEvents.cs w funkcji WeaponGrabIsOver() wywołaj ją z argumentem false