Do wirtualnej kamery przypisuję obiekt aim(obiekt który jest tam gdzie mysz)

W PlayerAim.cs
```
[SerializeField] private float minCameraDistance;
[SerializeField] private float maxCameraDistance;
[SerializeField] private float aimSensivity;
```

```
private Vector3 DesiredAimPosition()
{
    Vector3 desiredAimPosition = GetMousePosition();
    Vector3 aimDirction = (desiredAimPosition - transform.position).normalized;

    float distanceToDesiredPosition = Vector3.Distance(transform.position, desiredAimPosition);
    if(distanceToDesiredPosition > maxCameraDistance)
    {
        desiredAimPosition = transform.position + aimDirction * maxCameraDistance;
    }
    else if(distanceToDesiredPosition < minCameraDistance)
    {
        desiredAimPosition = transform.position + aimDirction * minCameraDistance;
    }
    desiredAimPosition.y = transform.position.y + 1;
    return desiredAimPosition;
}
```
Funkcja normalizuje pozycje myszy by wartość 1 wektora przemnożyć przez maksymalny dystans i sprawdzić czy nie jest to poza nim