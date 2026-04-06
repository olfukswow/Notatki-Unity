### Utworzenie klasy
Tworzymy nowy skrypt Weapon.cs i usuwamy z niego dziedziczenie z klasy MonoBehaviour (to ona dostarcza funkcje takie jak update, w skrócie ta klasa łączy skrypt z obiektami unity)

Dodajemy ten header na samym początku skryptu:
``[System.Serializable] // To pozwala na edytowanie tej klasy w inspektorze Unity``

### Przykładowe użycie klasy w PlayerWeaponController.cs
``    [SerializeField] Weapon currentWeapon;``

W Start():
`` currentWeapon.ammo = currentWeapon.maxAmmo;``
W Shoot():
```
if(currentWeapon.ammo <= 0)
    return;

currentWeapon.ammo--;
```




### Rozbudowa działania klasy Weapon
```
public enum WeaponType{
    Pistol,
    Rifle,
    Shotgun
}
public class Weapon
{
    public WeaponType weaponType;
    public int ammo;
    public int maxAmmo;
}
```