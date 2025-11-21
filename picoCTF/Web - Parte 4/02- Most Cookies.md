# Descripción
El reto es una aplicación web simple que utiliza **sesiones de Flask** (almacenadas en cookies firmadas) para rastrear la autenticación del usuario. Para obtener la *flag*, el usuario debe lograr que la variable de sesión `very_auth` contenga el valor **`admin`**.

Al analizar el código `server.py` se identifica lo siguiente:
1.  La *flag* se revela si `session["very_auth"] == "admin"` [Línea 74].
2.  La clave secreta (`app.secret_key`) utilizada para firmar la cookie se elige **aleatoriamente** de una lista predefinida de nombres de galletas (`cookie_names`) en cada inicio del servidor [Línea 10].
3.  La lista de posibles claves secretas (`cookie_names`) está disponible en el código fuente [Línea 6].

# Solución
La solución es un ataque de **fuerza bruta** al secreto de Flask (`secret_key`) para falsificar la cookie de sesión.

1.  **Identificar el Vector de Ataque:** La aplicación Flask utiliza cookies de sesión firmadas. Para falsificarlas, se necesita:
    * El contenido de la *cookie* deseado (el *payload*): `{"very_auth":"admin"}`.
    * La **clave secreta** (`secret_key`) correcta.
2.  **Obtener el Diccionario de Claves:** Se descarga y analiza el archivo `server.py` para obtener la lista completa de posibles claves secretas (`cookie_names`).
    * *Ejemplo de una clave:* **`peanut butter`** o **`fortune`**.
3.  **Fuerza Bruta de la Clave:** Se utiliza una herramienta automatizada (como **`flask-unsign`** dentro de un *script* de Python, `exploit.py`) para probar todas las claves secretas de la lista contra la *cookie* actual.
    * El script intenta firmar el *payload* deseado con cada clave y luego envía la *cookie* resultante al servidor para ver cuál devuelve la *flag*.
4.  **Ejecución y Éxito:** El script automatizado identifica el secreto correcto (e.g., `fortune`), genera una nueva cookie de sesión firmada con el *payload* `{"very_auth":"admin"}` y obtiene la *flag*.

**Paso a paso de la Terminal:**
* Instalación de herramientas: `pip install flask-unsign requests`
* Descarga del código fuente (para el diccionario de claves): `wget https://mercury.picoctf.net/static/.../server.py`
* Ejecución del exploit (que itera sobre el diccionario de claves y prueba las cookies firmadas): `python3 exploit.py`

**Resultado Final:**
* **Secreto correcto encontrado:** `fortune` (en la última ejecución)
* **Cookie firmada generada:** `eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.aRu5CQ.zJJUM7T7pkWnV3uJd5yFfp8Z0Q0`
* **Flag:** `picoCTF{pwn_4ll_th3_cook1E5_25bdb6f6}`

# Notas adicionales
Este reto es un ejemplo de cómo una seguridad inadecuada de la clave secreta (`secret_key`) en aplicaciones web construidas con frameworks como **Flask** puede llevar a la falsificación de sesiones. Si el `secret_key` puede ser adivinado o está en una lista conocida (como la lista de nombres de galletas en este caso), un atacante puede crear cualquier *cookie* de sesión válida. El uso de **`flask-unsign`** simplifica la automatización de este ataque de diccionario.

# Referencias
* `server.py` (código fuente analizado)
* Uso de `flask-unsign` (herramienta de fuerza bruta para secretos de Flask)