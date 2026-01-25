1. Stwórz obiekt 3d cube o nazwie bullet i nadaj mu odpowiednie rozmiary xyz np. 0.03, 0.03, 0.2
2. Dodaj rigidbody do obiektu bullet i w ustaw. rigidbody wyłącz "use gravity" i collsion detection na "continous" oraz dodaj nowy skrypt Bullet.cs
3. Przeciągnij ten gameObject do jakiegoś folderu w eksploratorze unity, teraz możesz już usunąć z świata gry pocisk gdyż mamy go w plikach jako prefab
4. Teraz w skrypcie obsługującym broń (WeaponController.cs) dodajemy zmienne
   - ``[SerializeField] private GameObject bulletPrefab;``
   - ``[SerializeField] private float bulletSpeed;``
   - ``[SerializeField] private Transform firePoint;``(miejsce lufy, skąd ma wylatywać pocisk)
1. W obiekcie gry WeaponHolder stwórz jako child każdej z broni empty object i nazwie firePoint i ustaw go w miejscu w którym ma wylatywać pocisk
2. W funckcji strzału w WeaponController dodaj następujący kod:
```
GameObject newBullet = Instantiate(bulletPrefab, firePoint.position, Quaternion.LookRotation(firePoint.forward));
newBullet.GetComponent<Rigidbody>().velocity = firePoint.forward * bulletSpeed;
Destroy(newBullet, 5); // Usunięcie stworzonego pocisku po 5 sekundach
```
3. W eksploratorze naciśnij na obiekt bullet i w jego inspektorze dodaj mu komponent "Trail rendererer" i jego wykres przeciągnij tak by koniec był równy 0.000 a początek około 0.025 a w ustawieniu material ustaw mu materiał takiego koloru jakiego chciałbyś by była smuga pocisku
4. W skrypcie Bullet.cs:
```
private Rigidbody rb => GetComponent<Rigidbody>();
private void OnCollisionEnter(Collision collision)
{
    rb.constraints = RigidbodyConstraints.FreezeAll;
}
```
5. Dodajemy layer "Player" i "Bullet" i obiektowi player oraz prefabowi bullet je odpowiednio nadajemy następnie na pasku/toolbarze: Edit > Project settings > Physics i na samym dole ustawiamy to tak jak na zdjęciu
 ![[Pasted image 20260109131830.png]]
 Jest to ustawienie co z czym może colidować czyli właśnie ustawiliśmy że bullet nie może collidować z bulletem i graczem