Object pool optymalizuje grę poprzez przetrzymywanie np. pocisków i włączanie ich i włączenie zamiast respienia i usuwania(destroy)

```
public static ObjectPool instance;

private void Awake(){
if(instance == null)
instance = this;
else
Destroy(instance);
}
```
Funkcje Object poola(obiektu nazwanego ObjectPool z przypisanym tym skryptem) można wywoływać wszędzie w innych skryptach bez referencji np:
``ObjectPool.instance.Funkcja()``

## Logika pocisków
```
[SerializeField] private GameObject bulletPrefab;
[SerializeField] private int poolSize = 10;
private Queue<GameObject bulletPool;

public GameObject GetBullet(){
GameObject bulletToGet = bulletPool.Dequeue();
bulletToGet.SetActive(true);
}

private void CreateInitialPool(){
for(int i = 0; i < poolSize;i++)
{
GameObject newBullet = Instantiate(bulletPrefab);
newBullet.SetActive(false);
bulletPool.Enqueue(newBullet);
}
}
```
(Do awake dodajemy przypisanie queue -``bulletPool = new Queue<GameObject()``)
``)

### Przykładowe użycie w funkcji strzału
```
GameObject newBullet = ObjectPool.instance.GetBullet();
newBullet.transform.position = wektorZPozycjaBulleta;
newBullet.transform.rotation = Quanternion.LookRotation(wektorZPozycjaBulleta.forward); //skierowanie bulleta w kierunku
```

### Funkcja object poola zastępująca destroy wywoływana w funkcji shoot
```
public void ReturnBullet(GameObject bullet){
bullet.SetActive(false);
bulletPool.Enqueue(bullet);

}
```

## Zapranetowanie bulletów by grupować
```
public void ReturnBullet(GameObject bullet){
bullet.SetActive(false);
bulletPool.Enqueue(bullet);
bullet.transform.parent = transform; // bullet ponowne staje sie childem aktualnego transforma czyli object poola
}
```
```
public GameObject GetBullet(){
GameObject bulletToGet = bulletPool.Dequeue();
bulletToGet.SetActive(true);
bulletToGet.transform.parent = null; // bez parenta - bedzie sam na liscie obiektow
}
```
```
private void CreateInitialPool(){
for(int i = 0; i < poolSize;i++)
{
GameObject newBullet = Instantiate(bulletPrefab, transform);// drugi argument to transform ktory ma byc parentem obiekt tworzony
newBullet.SetActive(false);
bulletPool.Enqueue(newBullet);
}
}
```


## Dodawanie nowych obiektow gdy ich braknie

```
GameObject newBullet = Instantiate(bulletPrefab, transform);// drugi argument to transform ktory ma byc parentem obiekt tworzony
newBullet.SetActive(false);
bulletPool.Enqueue(newBullet);
```
Ten kod wrzucamy do funkcji CreateBullet()

```
if(bulletPool.count == 0)
CreateBullet(); 


public GameObject GetBullet(){
GameObject bulletToGet = bulletPool.Dequeue();
bulletToGet.SetActive(true);
bulletToGet.transform.parent = null; // bez parenta - bedzie sam na liscie obiektow
}
```
Tu dodajemy ifa tworzącego bulleta gdy queue jest pusty