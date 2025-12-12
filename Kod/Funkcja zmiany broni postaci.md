Do Weapon_Holder dodajemy komponent - Skrypt do kontrolowania wizualek broni czyli przykładowa nazwa to WeaponVisualController

W tym skrypcie:
``[SerializeField] private Transform[] gunTransforms;``
 Jest to tablica obiektów którymi będziemy transformować każdą z broni z Weapon_Holder którą oczywiście przypisujemy poprzez przeciągnięcie każdego z obiektów broni do tej tablicy w inspektorze Weapon holdera

#### Funkcja wyłączania wszystkich broni
```
private void SwitchOffGuns()
{
    for (int i = 0 ; i < gunTransforms.Length; i++)
    {
        gunTransforms[i].gameObject.SetActive(false);
    }
}
```

#### Funkcja wyboru broni
```
private void SwitchOn(Transform gunTransform)
{
    SwitchOffGuns();
    gunTransform.gameObject.SetActive(true);
}
```
##### Użycie funkcji wyboru broni
```
private void Update()
{
    if(Input.GetKeyDown(KeyCode.Alpha1))
    {
        SwitchOn(gunTransforms[0]);
    }
    else if(Input.GetKeyDown(KeyCode.Alpha2))
    {
        SwitchOn(gunTransforms[1]);
    }
    else if(Input.GetKeyDown(KeyCode.Alpha3))
    {
        SwitchOn(gunTransforms[2]);
    }
    else if(Input.GetKeyDown(KeyCode.Alpha4))
    {
        SwitchOn(gunTransforms[3]);
    }
    else if(Input.GetKeyDown(KeyCode.Alpha5))
    {
        SwitchOn(gunTransforms[4]);
    }
}
```