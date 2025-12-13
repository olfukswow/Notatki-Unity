- Stwórz skrypt PlayerAim.cs i dodaj go jako komponent obiektu gracza
- W skrypcie Player.cs (odpowiedzialny za chociażby stworzenie obiektu PlayerControls) stwórz obiekt klasy PlayerAim
``public PlayerAim aim { get; private set; }``

W Funkcji awake skryptu Player.cs:
`` aim = GetComponent<PlayerAim>(); // czyli ta klasa musi być komponentem w tym samym GameObject``

W klasie PlayerAim.cs
```
private Player Player;
private PlayerControls controls;

private Vector2 aimInput;
private void Start()
{
    Player = GetComponent<Player>();
    AssignInputEvents();
}

private void AssignInputEvents()
{
    controls = Player.controls;

    controls.Character.Aim.performed += ctx => aimInput =        ctx.ReadValue<Vector2>();
    controls.Character.Aim.canceled += ctx => aimInput = Vector2.zero;
}
```


Dodajemy kolejne zmienne i funkcję do zwracania pozycji myszy
```
[Header("Aim info")]
[SerializeField] private LayerMask aimLayerMask;
[SerializeField] private Transform aim;
private Vector3 lookingDirection;
```
```
 public Vector3 GetMousePosition()
 {
     Ray ray = Camera.main.ScreenPointToRay(aimInput);
     if(Physics.Raycast(ray, out RaycastHit hitInfo, Mathf.Infinity, aimLayerMask))
     {
         return hitInfo.point;
     }
     return Vector3.zero;
 }
```
(zmienna aim to referencja do obiektu który ma wskazywać w świecie gry miejsce celowania a aimLayerMask to layery do wybrania które mają się liczyć jako obiekt na którym myszka jak jest to ma być wyliczona jej lokalizacja)
##### Użycie tej funkcji w skrypcie player movement opowiedzianym za obrót postaci w kierunku myszki
```
private void ApplyRotation()
{
       Vector3 lookingDirection = player.aim.GetMousePosition() - transform.position;
        lookingDirection.y = 0;
        lookingDirection.Normalize();
        transform.forward = lookingDirection;
}
```