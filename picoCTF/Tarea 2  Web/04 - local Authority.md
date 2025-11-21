# Descripción  
Este reto consiste en encontrar credenciales expuestas dentro de los archivos del sitio web para poder iniciar sesión y obtener la flag. El desafío se basa en una mala práctica común: dejar información sensible dentro de archivos JavaScript accesibles públicamente, lo que permite descubrir usuario y contraseña sin necesidad de vulnerar el sistema.

# Solución  
1. Intentar un inicio de sesión cualquiera para observar el comportamiento del sistema.  
2. Inspeccionar el código fuente de la página principal (`Ctrl+U`) y revisar el formulario que envía la solicitud a **login.php**.  
3. Realizar una solicitud directa a **login.php** para ver si hay redirecciones o pistas adicionales.  
4. Revisar todos los archivos referenciados en el HTML.  
5. Localizar **secure.js**, archivo que contiene las credenciales en texto plano.  
6. Utilizar esas credenciales para iniciar sesión en la página.  
7. Acceder al panel y obtener la flag mostrada en la interfaz.

# Notas adicionales  
- Este tipo de error es extremadamente común en desarrollos principiantes: dejar claves o tokens en archivos JS pensando que “no se ven”.  
- En realidad, todo lo que está en el front-end es público, sin excepción.  
- La solución no requiere fuerza bruta ni explotación avanzada, solo inspección del código.  
- Es un reto clásico de *Web Exploitation* ideal para principiantes.

# Referencias  
- Video: *local Authority | picoCTF 2022* — Canal: Rahul Singh Chauhan  
- Publicado: 9 abril 2022  
- URL del video: http://www.youtube.com/watch?v=PgYT8FX4Jm8  
- Contenido accesible: http://googleusercontent.com/youtube_content/2
