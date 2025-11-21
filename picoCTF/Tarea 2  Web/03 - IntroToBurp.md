# Descripción  
Este reto introduce el uso de **Burp Suite** dentro del contexto de **Web Exploitation** en picoCTF 2024. El objetivo principal es aprender a interceptar, analizar y modificar las peticiones HTTP/S enviadas por el navegador hacia el servidor, con el fin de descubrir información, manipular parámetros o desbloquear comportamientos que permitan obtener la flag.  
El video funciona como una demostración rápida del flujo básico de trabajo con Burp Suite.

# Solución  
1. Abrir Burp Suite y activar **Proxy → Intercept ON**.  
2. Configurar el navegador para que use el proxy de Burp (generalmente 127.0.0.1:8080).  
3. Acceder a la página del reto en picoCTF.  
4. Dejar que Burp capture la primera petición y revisarla en **HTTP history**.  
5. Identificar parámetros, cookies o valores modificables.  
6. Editar la petición si es necesario (con **Intercept** o **Repeater**).  
7. Enviar la petición manipulada al servidor para obtener una respuesta distinta.  
8. Revisar la salida devuelta (HTML, JSON, encabezados, etc.) hasta localizar la flag.  
9. Copiar la flag y enviarla en la plataforma de picoCTF.

# Notas adicionales  
- Burp Suite es una herramienta estándar en pruebas de penetración web.  
- Permite automatizar ataques simples y complejos: manipulación de formularios, fuzzing, análisis de cookies o tokens, entre otros.  
- En retos “IntroToBurp”, generalmente la flag se obtiene modificando un valor o capturando una petición que normalmente no se ve en el navegador.  
- Es recomendable usar Burp Community Edition, suficiente para este tipo de ejercicios.

# Referencias  
- Video base: *IntroToBurp | Web Exploitation | picoCTF 2024* — get__pismed  
- Fecha de publicación: 8 abril 2024  
- URL del video: http://www.youtube.com/watch?v=K5jxNaEKcXs  
- Contenido accesible: http://googleusercontent.com/youtube_content/1
