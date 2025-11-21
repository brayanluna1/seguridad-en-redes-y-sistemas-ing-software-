# Descripción
El video es un walkthrough que muestra la resolución del desafío “Red” de la categoría de Informática Forense (Forensics) en picoCTF 2025. El reto proporciona un archivo de imagen llamado `red.png` junto con algunas pistas iniciales.

# Solución
1. Se revisan las pistas del desafío, incluyendo una referencia a “check whatever Facebook is called now”, lo cual apunta a Meta.
2. Se descarga el archivo `red.png` usando `wget` desde el webshell del entorno de picoCTF.
3. Debido a que el reto pertenece a Forensics y utiliza una imagen, se plantea la hipótesis de esteganografía.
4. Se usa la herramienta `steg` (`is stg`) para examinar el contenido oculto dentro de `red.png`.
5. La herramienta revela un poema acompañado de una cadena codificada en Base64.
6. Se copia la cadena Base64 y se decodifica en línea usando b64decoder.org, obteniendo así la flag del desafío.

# Notas adicionales
La clave del reto es identificar el uso de esteganografía y utilizar una herramienta adecuada para extraer la información oculta antes de decodificar la cadena Base64 resultante.

# Referencias
- Video original: PICO CTF 2025 - Red | Forensics | CyberSecurity — I am Kronus  
  URL: http://www.youtube.com/watch?v=2nXdSCkeS4I
- Fuente del contenido en bruto: http://googleusercontent.com/youtube_content/12
