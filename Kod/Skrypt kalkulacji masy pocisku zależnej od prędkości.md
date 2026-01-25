Najpierw przetestuj różne masy pocisku i dobierz tę która przy aktualnej prędk. pocisku najrealniej oddaje odpychanie obiektów

W PlayerWeaponController.cs
```
 private const float REFERENCE_BULLET_SPEED = 20f;
 // Domyślna wart. prędkość pocisku do której skalowane są inne wartości
```

W funkcji strzału w tym samym skrypcie przed nadaniem kuli wartości velocity
```
Rigidbody rb = newBullet.GetComponent<Rigidbody>();
// new bullet to obiekt typu gameObject = Instantiate
rb.mass = REFERENCE_BULLET_SPEED / bulletSpeed;
```

Dzięki temu nawet przy zwiększeniu prędkości kuli masa zostanie tak przeskalowana by inne obiekty przy kolizji z kulą odlatywały tak samo