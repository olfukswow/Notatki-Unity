W PlayerWeaponController.cs
```
[Header("Inventory")]
[SerializeField] private List<Weapon> weaponsInventory = new List<Weapon>();
```
Do Input Manager dodajemy przyciski do wybierania broni, czyli np. dodajemy przycisk numeryczny 1 i 2 oraz przycisk do wyrzucania broni np. G

W PlayerWeaponController.cs
```
private void EquipWeapon(int index)
{
    currentWeapon = weaponsInventory[index];
}
public void DropWeapon()
{
    if(weaponsInventory.Count <= 1)
        return;
    weaponsInventory.Remove(currentWeapon);
    currentWeapon = weaponsInventory[0];
}
```
W metodzie update:
```
player = GetComponent<Player>();
player.controls.Character.EquipSlot1.performed += ctx => EquipWeapon(0);
player.controls.Character.EquipSlot2.performed += ctx => EquipWeapon(1);
player.controls.Character.DropCurrentWeapon.performed += ctx => DropWeapon();
```
