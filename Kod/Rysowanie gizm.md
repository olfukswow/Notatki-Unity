```
public void onDrawGizmos(){
Gizmos.DrawLine(weaponHolder.position, weaponHolder.forward * 25);
Gizmos.color = Color.yellow;
}
```
zmienna weaponHolder to zmienna typu transform, pierwszy argument to skąd ma być rysowana linia a druga to dokąd.