``public CharacterController characterController;``
(gameObject na którym jest skrypt musi zawierać atrybut Character Controller)
W inpsektorze do  zmiennej characterController przypisuje atrbut CharacterController z obiektu który ma być sterowany
lub przypisuje do zmiennej gdy jest prywatna i chcę przypisać atrybut z obiektu na którym jest skrypt w następujący sposób
``characterController = GetComponent<CharacterController>();``



``characterController.Move(movementDirection);``
Ruch postaci
