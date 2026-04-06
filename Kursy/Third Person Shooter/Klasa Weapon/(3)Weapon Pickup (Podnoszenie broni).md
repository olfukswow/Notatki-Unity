Tworzymy nowy skrypt o nazwie np. ItemPickupSystem.cs

W PlayerWeaponController.cs:
```
private void PickupWeapon(Weapon newWeapon)
{
    if(weaponsInventory.Count >= maxSlotsAllowed)
        return;
    weaponsInventory.Add(newWeapon);
}
```
(zmienna maxSlotsAllowed to Seralized zmienna w tej klasie)

W ItemPickupSystem.cs:
```
public class ItemPickupSystem : MonoBehaviour
{
    [SerializeField] private Weapon weapon;
    private void OnTriggerEnter(Collider other)
    {
        other.GetComponent<PlayerWeaponController>()?.PickupWeapon(weapon);
    }
}
```