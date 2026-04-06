https://assetstore.unity.com/vfx
W naszym przypadku użyjemy assetu https://assetstore.unity.com/packages/vfx/particles/spells/magic-effects-free-247933
![[Pasted image 20260127110000.png]]By go użyć naciskamy "Add to my assets"
Następnie w edytorze przechodzimy do packet managera(Window > Package Manager)
I Wybieramy go z listy "My assets" Po czym naciskamy Download/Import
Następnie konwertujemy te efekty do URP poprzez Window > Rendering > Render Pipeline Converter

W eksploratorze pików unity efekty znajdziemy w folderze Hovl Studio > Magic effects
(Przy użyciu danego efektu po przeciągnięciu go do świata gry w liście obiektów naciśnij PPM > Prefab > Unpack Completely), Jeśli przed chcesz zmienić jego właściwości np. rozmiary zapisać go tak by każdy obiekt miał te właśc. to przed rozpakowaniem ustaw je a następnie w inpsektorze prefaba naciśnij "overrides" i wybierz "Apply all"

W skrypcie Bullet.cs
  ``[SerializeField] private GameObject bulletImpact;``
  (Przypisujemy obiekt VFX który ma się odtworzyć przy kontakcie)

```
private void OnCollisionEnter(Collision collision)
{
    if (collision.contacts.Length > 0)
    {
        ContactPoint contact = collision.contacts[0];
        GameObject impactEffect = Instantiate(bulletImpact, contact.point, Quaternion.LookRotation(contact.normal));
        Destroy(impactEffect, 1f);
    }
}
```