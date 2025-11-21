# Descripción
El reto gira en torno a una aplicación web llamada "JaWT Scratchpad" que utiliza **JSON Web Tokens (JWT)** para gestionar las sesiones de usuario. La meta es acceder al *scratchpad* (bloc de notas) especial del usuario `admin`, el cual está protegido. La descripción del reto es: "Check the admin scratchpad." [00:00:20].

# Solución
La solución es un ataque de **falsificación de JWT (JWT Forgery)**, explotando una clave secreta débil utilizada para firmar el token.

1.  **Obtener JWT:** Inicie sesión con cualquier nombre de usuario que no sea `admin` (e.g., `HackerFrogs`). Utilice las herramientas de desarrollador del navegador (`Storage`) para copiar el valor de la *cookie* llamada **`JWT`** [00:03:54].
2.  **Análisis Inicial:** Utilice un decodificador en línea (como `jwt.io`) para pegar el token y verificar que el *payload* contiene la clave `user` con su nombre de usuario (e.g., `{"user":"hackerfrogs"}`) [00:05:57].
3.  **Fuerza Bruta de la Clave Secreta:**
    * Guarde el token JWT en un archivo de texto (e.g., `jwt.txt`) [00:08:31].
    * Utilice **John the Ripper** (o una herramienta similar) para realizar un ataque de diccionario contra el token y descubrir la clave secreta de firma, usando un *wordlist* común (e.g., `rockyou.txt`) [00:09:12].
    * La clave secreta descubierta es **`I love Pico`** [00:09:54].
4.  **Forjar Nuevo JWT:**
    * Vuelva al decodificador JWT y modifique el *payload* para cambiar el valor del usuario a **`admin`** (`{"user":"admin"}`) [00:06:58].
    * Ingrese la clave secreta descubierta (**`I love Pico`**) en el campo de *Verificación de Firma* [00:10:21].
    * Copie el nuevo token JWT generado (falsificado).
5.  **Explotación:** Reemplace el valor de la *cookie* **`JWT`** en el navegador con el nuevo token falsificado [00:10:54]. Recargue la página para acceder al *scratchpad* del administrador y obtener la *flag* [00:11:10].

# Notas adicionales
Este es un caso clásico de **manipulación de tokens de sesión**. La vulnerabilidad clave reside en la debilidad de la **clave secreta (HMAC Secret)** utilizada para firmar el JWT. Si la clave es fácil de adivinar o se encuentra en un diccionario, un atacante puede falsificar tokens válidos cambiando los datos del *payload* (como el nombre de usuario) y volviendo a firmar el token, eludiendo la autenticación.

# Referencias
[picoCTF 2019 - Web App - JaWT Scratchpad - JWT Forgery](http://www.youtube.com/watch?v=xAjm8LqRiCI)