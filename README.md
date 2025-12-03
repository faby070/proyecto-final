# proyecto-final
RESUMEN FINAL DEL PROYECTO.

Este proyecto consiste en un sistema web de registro, login y recuperación de contraseña completamente funcional y seguro.
Durante el registro, se validan los datos del usuario mediante expresiones regulares, asegurando que el nombre tenga formato correcto, 
el correo sea válido y el número de móvil pertenezca a Bolivia. La contraseña debe cumplir con un mínimo de caracteres. 
En el login, se lleva un control de los intentos fallidos, bloqueando la cuenta después de tres errores consecutivos y mostrando un 
enlace para recuperar la contraseña. Al recuperar la contraseña, el usuario puede crear una nueva, que se valida automáticamente, y al 
actualizarla se desbloquea la cuenta y se reinician los intentos fallidos. Todo el sistema utiliza localStorage para almacenar los datos, 
garantizando que el usuario pueda iniciar sesión de manera segura y sencilla, mientras se mantiene un flujo completo de registro, acceso 
y recuperación de contraseña.

1. USO DE EXPRESIONES REGULARES

En el proyecto se utilizan expresiones regulares para validar los datos del usuario durante el registro. Por ejemplo, para el nombre 
completo se exige que tenga nombre y dos apellidos con mayúscula inicial:
/^[A-Z][a-zA-Z]+(?:\s[A-Z][a-zA-Z]+){2}$/
Esto garantiza que el usuario ingrese datos con el formato correcto. De igual manera, se valida que el correo tenga el formato estándar 
usuario@dominio.com y que el número de móvil sea válido en Bolivia. Las expresiones regulares permiten validaciones rápidas y confiables 
sin necesidad de código largo.

2. MANEJO DEL BLOQUEO

El sistema lleva un registro de los intentos fallidos de inicio de sesión utilizando localStorage. Cada vez que el usuario ingresa mal 
la contraseña, se incrementa un contador.
Al llegar a 3 intentos fallidos, se bloquea la cuenta y se muestra el mensaje:
"Cuenta bloqueada por intentos fallidos."
Además, se activa un enlace para recuperar la contraseña. Esto evita accesos no autorizados y protege la seguridad de la cuenta.

3. COMO SE VALIDA LA CONTRASEÑA

La contraseña se valida con una regla mínima de seguridad. En este proyecto, se exige que la contraseña tenga al menos 4 caracteres 
mediante la expresión regular:
/.{4,}/
Esto se aplica tanto en el registro como en la recuperación de contraseña. Si el usuario no cumple la regla, el sistema muestra un 
mensaje de error y no permite continuar, garantizando que siempre haya un formato válido.

4. COMO SE ACTUALIZA LA CONTRASEÑA OLVIDADA

Cuando la cuenta se bloquea, el usuario puede hacer clic en “Recuperar contraseña”, lo que abre un formulario para crear una nueva 
contraseña.
El sistema valida la nueva contraseña con la misma regla que el registro y, una vez correcta:
Se actualiza la contraseña en localStorage.
Se desbloquea la cuenta automáticamente.
Se reinicia el contador de intentos fallidos a cero.
Finalmente, el sistema muestra el mensaje:
"Contraseña actualizada. Ahora puede iniciar sesión."
Esto permite que el usuario recupere el acceso de manera segura y sencilla
