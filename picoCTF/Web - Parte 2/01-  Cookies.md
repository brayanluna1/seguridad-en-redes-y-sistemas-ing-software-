
# Descripción
El reto, titulado "Cookies", consiste en encontrar la "galleta especial" ("special cookie") en un sitio web que simula una búsqueda de galletas. La descripción del desafío es: "A quién no le encantan las galletas, intenta descubrir la mejor. La solución requiere manipular una cookie HTTP para forzar una respuesta anómala del servidor que revele la *flag*.

# Solución
1.  **Inspección de Cookies:** Se accede a las herramientas de desarrollador del navegador (Dev Tools) y se identifica una cookie HTTP llamada `name` con un valor numérico (e.g., `-1`, `0`, `1`) [00:00:55]. Se verifica que cambiar el valor de la cookie resulta en diferentes mensajes de "galleta" [00:01:14].
2.  **Automatización con Burp Suite:** Se utiliza la herramienta Burp Suite, específicamente la función **Intruder**, para automatizar el proceso de prueba de valores para la cookie `name` [00:01:41].
3.  **Configuración del Ataque:** Se intercepta una solicitud HTTP y se envía a Intruder. Se marca el valor de la cookie `name` como el *payload position* (posición de carga útil). En la sección *Payloads*, se selecciona el tipo **Numbers** (Números) para probar un rango secuencial, por ejemplo, de `-1` a `100`, con un paso de `1` [00:02:19].
4.  **Análisis de Respuestas:** Al ejecutar el ataque, se analizan los resultados prestando especial atención a la columna **Length** (Longitud de Contenido). La mayoría de las cookies válidas tienen un código de estado `200` y una longitud de contenido similar.
5.  **Identificación de la Flag:** Se detecta que el valor **18** devuelve una longitud de contenido significativamente menor [00:03:05], lo que indica que el servidor está enviando una respuesta diferente. Al cambiar manualmente el valor de la cookie `name` a `18` y recargar la página, se obtiene la *flag* [00:03:16].

# Notas adicionales
Este es un ejercicio común de **Cookie Tampering** (manipulación de cookies) dentro de la categoría de Web Exploitation. La clave de la solución es el uso de una herramienta de proxy (Burp Suite) para automatizar el *fuzzing* de un parámetro (el valor numérico de la cookie) y analizar las respuestas del servidor para encontrar una anomalía que no es visible a simple vista.

# Referencias
[How Hackers Tamper Cookies to Find Hidden Data | picoCTF Cookies](http://www.youtube.com/watch?v=yDUWhuM5HhQ)