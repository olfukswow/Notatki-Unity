Window > Packet Manager > Unit Registry -> Input System (nazwa paczki)
Edit > Project Settings > Player > Other settings > Active Input Handling ma być ustawiony najlepiej na both

### Utworzenie akcji inputu
W eksploratorze plików w edytorze unity PPM > Create > Input Actions ( na samym dole listy)
### Zarządzanie inputem
W eksploratorze klikasz na plik Input Actions i w menu po prawej naciskasz edit asset
#### Action maps
Action mapy to zestaw inputów zależnych, np. jak w gta gdy jesteś na lądzie to chcesz by np przycisk ruchu wywoływał inną czynność niż gdy jest w wodzie, czyli dla tych dwóch sytuacji tworzysz dwie różne action mapy
#### Actions
Jak nazwa wskazuje, po utworzeniu PPM na akcje > Add binding, ten binding to przycisk który ma być powiązany z tą akcją


```
private PlayerControls controls;
 private void Awake()
 {
     controls = new PlayerControls(); 
     controls.Character.Fire.performed += ctx => FuncjaDoWywolania(); 
 }
 private void FuncjaDoWywolania()
 {
     Debug.Log("Funkcja wywolana");
 }
```

#### .Fire - nazwa stworzonej przez ciebie akcji
#### .performed - tyczy się sytuacji wywołania akcji 
#### ctx => wskazuje na kod który ma zostać wywołany w tym przypadku
### W przypadku wektora
```
controls.Character.Movement.performed += ctx => moveInput = ctx.ReadValue<Vector2>();
```
Gdzie move input to stworzona zmienna typu vector2
### Przypadek z paroma linijkami kodu do wykonania w ctx
```
controls.Character.Run.performed += ctx => { 
    isRunning = true; 
    speed = runSpeed;
};
```

[[Wykorzystanie zaawansowanego input systemu w kodzie|Wykorzystanie w kodzie]]
