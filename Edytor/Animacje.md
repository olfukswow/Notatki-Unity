(Kurs 21)
Do obiektu który ma być animowany dodaj component Animator
W dowolnym folderze(zalecany to Animations/Animator Controller) stwórz AnimatorController i przeciągnij go do pola Animator Controller w Animatorze w obiekcie 
Element avatar z pliku fbx animacji(dostępne po naciśnięciu strzałki przy pliku) przeciągnij do pola Avatar w Animatorze w obiekcie

(W przypadku animacji dla postaci humanoidalnej w inspektorze animacji w zakładce rig wartość animation type musi być ustawione na humanoid. Jeśli animacja ma się powtarzać wartość loop time w zakładce animation musi być ustawiona na true. Aby upewnić się iż przód animacji jest ustawiony w odpowiednim kierunku w zakładce animation w miejscu "Root Transform Rotation" ustaw na true wartość Bake Into Pose oraz Based Upon na wartość original)

## Dodawanie animacji do controllera
Aby dodać animację do controllera przeciągnij plik animacji do pustej przestrzeni okna animatora. W przypadku braku innych animacji zostanie ona od razu przywiązana do Entry co oznacza iż będzie ona animacją domyślną

## Ustawianie wartości parametrów blendera
`` private Animator animator;``
``animator.SetFloat("nazwaParametruZEdytora", wartosc);``
``animator.SetFloat("zVelocity", zVelocity, 1f, Time.deltaTime);`` 
wersja z 4 parametrami różni się tym iż trzeci parametr definiuje czas przejścia między animacjami


## Łączenie animacji góry i dołu w jedną
- W animatorze w zakładce layers jedna musi być dla animacji dołu a druga dla animacji góry czyli ich nazwy to np. Common Weapon Layer (czyli góra - animacje trzymania broni) i Movement Layer


- W plikach stwórz avatar mask i w jego inpsektorze wybierz na czerwony części ciała(i napisy przy nich) które nie mają być animowane, zadbaj o to by nazwa sugerowała czego dotyczy maska czyli jeśli pozwala ona na animowanie góry to nazwij ją np Upper body avatar mask
- Waga layeru w jego ustawieniach powinna wynosić 1
- Ustaw w ustawieniu mask odpowiednią maskę
(gdy layer od góry ma maskę zezwalająca na animacje góry to layer movementu nie musi mieć maski)

[[(5)Animation layers|Animation Layers]]
