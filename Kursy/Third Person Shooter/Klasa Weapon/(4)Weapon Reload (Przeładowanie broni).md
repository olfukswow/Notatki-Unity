## Logika amunicji
W Weapon.cs
```
public bool CanShoot()
{
    return HaveEnoughBullets();
}

private bool HaveEnoughBullets()
{
    if (ammo > 0)
    {
        ammo--;
        return true;
    }
    return false;
}
```
W PlayerWeaponController.cs, w funkcji Shoot():
```
if(!currentWeapon.CanShoot())
    return; 
```


## Logika przeładowania broni
Najpierw w Input System dodajemy akcję "Reload" i dodajemy binda, zapewne przycisk R

W PlayerWeaponVisualsController.cs:
```
private void PlayReloadAnimation()
{
    if(isGrabbingWeapon)
        return;

        animator.SetTrigger("Reload");
        ReduceRigWeight();  
}
```
W PlayerWeaponController.cs (kod ten musi być wywołany w funkcji Start()):
```
 player.controls.Character.Reload.performed += ctx =>
{
    if (currentWeapon.CanReload())
    {
    player.weaponVisuals.PlayReloadAnimation();
    }
};
```
(weaponVisuals to obiekt klasy PlayerWeaponVisualsController w obiekcie player przypisywany w klasie player do ``GetComponent<PlayerWeaponVisualsController>``)
W Weapon.cs:
```
public bool CanReload()
{
if (ammo == maxAmmo)
    return false;
    if (totalReserveAmmo > 0)
        return true;
    return false;
}
public void ReloadBullets()
{
    int bulletsToReload = maxAmmo;
    if(bulletsToReload > totalReserveAmmo)
        bulletsToReload = totalReserveAmmo;

    totalReserveAmmo -= bulletsToReload;
    ammo = bulletsToReload;
    if(totalReserveAmmo < 0)
        totalReserveAmmo = 0;

}
```

W PlayerWeaponController.cs:
```
public Weapon CurrentWeapon() =>
    currentWeapon;
```

W PlayerAnimationEvents.cs:
``private PlayerWeaponController weaponController;``
``weaponController = GetComponentInParent<PlayerWeaponController>();``
```
public void ReloadIsOver()
{
    weaponVisualController.MaximizeRigWeight();
    weaponController.CurrentWeapon().ReloadBullets();

}
```
(Do funkcji po przeładowaniu dodajemy logike przeładowania w tym momencie)
