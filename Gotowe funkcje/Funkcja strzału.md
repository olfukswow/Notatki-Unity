```
private void Shoot()
{
    GameObject bullet = Instantiate(bulletPrefab, gunPoint.position, gunPoint.rotation);
    bullet.GetComponent<Rigidbody>().velocity = gunPoint.forward * bulletSpeed;
    Destroy(bullet, 5); // Usunięcie obiektu bo 5 sekundach
}
```
(bulletPrefab to zmienna typu GameObject do której jest przypisany prefab z plików, natomiast gunPoint to wektor broni z której strzelamy)