### ``void Update()``
#### Funkcja ``Update`` jest wywoływana co każdą klatkę w grze (np. w przypadku 120 FPS zostanie wywołana 120 razy w ciągu sekundy)
##### Wykorzystywana chociażby do inputów

### ``void Start()``
#### Funkcja Start jest wywołana tylko w pierwszej klatce

### ``void FixedUpdate()`` 
### Funkcja jest wywoływana co określony ustalony czas niezależnie od wartości FPS (Aby ustawić jej czas: Edit -> Project Settings -> Time -> Fixed Timestep - Wartość jest podana w sekundach)
##### (Wykorzystywana chociażby do movement'u)
