W klasie Weapon.cs:
```
public float fireRate = 1; // bullets per second
private float lastShootTime;
```

```
private bool IsReadyToFire(){
if(Time.time > lastShootTime + 1 / fireRate){
// if sprawdzajacy czy uplynela odpowiednia ilosc czasu dla fire rate
lastShootTime = Time.Time;
return true;
}
return false;
}
```
Do funkcji ``CanShoot()`` z klasy Weapon.cs dopisujemy do ifa sprawdzenie czy ``ReadyToFire``:
```
public bool CanShoot()
{
return HaveEnoughBullets() && ReadyToFire()
}
```