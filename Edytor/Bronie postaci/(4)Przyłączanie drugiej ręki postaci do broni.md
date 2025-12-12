Do obiektu Rig 1 dodaj nowy empty object i nazwij go LeftHand_IK i dodaj temu obiektowi Two Bone IK Constraint(po krótce ten komponent kalkuluje jak poruszyć pozostałe kości postaci by ruch całości wyglądał dobrze)

Do pola "Tip" w komponencie przeciągnij gameObject dłoni która ma być poruszana(w moim przypadku leftHand)
Następnie PPM na komponent > auto setup from tip transform

jako childy obiektu LeftHand_IK powstaje jego target i hint, target na którego to miejsce idzie ręka - czyli jakby ręka trzymała ten target, czyli gdy ręka ma trzymać broń to trzeba po prostu obiekt targeta "przykleić" do broni natomiast hint decyduje o pozycji ramienia

## Przyklejenie ręki do broni tak by podążała za jej ruchem

obiekty target i hint z LeftHand_IK przeciągnij do rightHand (tudzież lokalizacji Weapon holdera) tak by były one childami prawej ręki



## Działanie dla wielu różnych broni
dla każdej broni stwórz empty gameObject i wklej do niego transform IK targetu który dobrze wygląda na tej broni - w momencie zmiany na tą broń przypiszemy zapisane w nim transformy dzięki czemu będzie to wyglądać tak jak chcieliśmy

Stwórz skrypt LeftHandTargetTransform.cs i zostaw go jako pustą klasę i przypisz jako komponent w każdym z gameObjectów przechowujących transform

W weaponVisualControllerze - tam gdzie zmieniasz które bronie są aktywne
```
 [Header("Left Hand IK")]
 [SerializeField] private Transform leftHand;
 private Transform currentGun;
```
(w inspektorze weaponHoldera do leftHand przypisz obiekt LeftHand_IKTarget czyli obiekt targeta który jest przypisany do postaci)
oraz funkcja
```
private void AttachLeftHand()
{
    Transform targetTransform = currentGun.GetComponentInChildren<LeftHandTargetTransform>().transform;
    leftHand.localPosition = targetTransform.localPosition;
}
```
gdzie komponent szukany to wcześniej stworzony pusty skrypt

A do wcześniej utworzonej funkcji zmiany broni dodajemy wywołane tej funkcji by po zmianie broni był używany jej target:
```
 private void SwitchOn(Transform gunTransform)
 {
     SwitchOffGuns();
     gunTransform.gameObject.SetActive(true);
     AttachLeftHand();
 }
```