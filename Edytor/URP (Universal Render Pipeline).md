URP to zoptymalizowane narzędzie do renderowania

# Inicjalizacja URP w projekcie
Window > Packet Manager
Instalujemy poniższy pakiet
![[Pasted image 20260125113046.png]]
Window > Rendering > Render Pipeline Converter 
Wybieramy wszystkie opcje z listy, następnie naciskamy "Initialize And Convert"

W eksploratorze plików unity:
Create > Rendering > URP Asset(with Universal Renderer), nazwij go URP
Dla organizacji plików przenieś powstałe pliki do folderu o nazwie np. "URP Settings
"

Edit > Project settings > Graphics 
Scriptable Render Pipeline Settings ustaw na powstały plik o nazwie "URP"

Edit > Project settings > Quality
Render Pipeline Asset ustaw na powstały plik o nazwie "URP"

W edytorze przejdź do obiektu MainCamera w świecie gry i w jego inspektorze w zakładce rendering ustawienie "Post processing" przełącz na włączone

Do świata gry dodaj obiekt Volume (PPM na listę obiektów > Volume > Global volume) i przeciągnij ten obiekt na samą górę list obiektów, następnie w inspektorze tego obiektu przy ustawieniu "Profile" naciśnij przycisk New. Teraz aby dodawać obiekty Post processingu możesz w inspektorze tego obiektu wybrać opcję "Add override" i wybrać z menu dany efekt np. bloom
###### Obiekt ten pozwala na uruchamianie i zarządzanie efektami post processingu

[[Dodawanie efektu świecenia do obiektu]]