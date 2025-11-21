# Descripción  
El reto **Web Decode** consiste en identificar y decodificar datos ocultos mediante algún tipo de codificación común en aplicaciones web. La flag no suele estar visible directamente; está transformada mediante Base64, URL encoding, HTML entities u otro esquema simple. El objetivo es reconocer el tipo de codificación, revertirla y recuperar la información original. Este tipo de desafíos pertenece a la categoría **Web Exploitation**, donde se analizan elementos del lado del cliente para descubrir contenido oculto o manipulado.

# Solución  
1. Abrir la página del reto e inspeccionar el código fuente o los elementos visibles desde DevTools.  
2. Localizar cadenas sospechosas: caracteres `%xx`, `=`, `/`, `&`, secuencias largas de caracteres mixtos o patrones típicos de Base64.  
3. Identificar el tipo de codificación (Base64, URL, HTML entities, ROT, etc.).  
4. Usar herramientas como:  
   - CyberChef  
   - base64decode.org  
   - URL/HTML decoder (DevTools → Console → `decodeURIComponent()` o `he.decode()`)  
5. Aplicar la decodificación necesaria hasta revelar la flag completa.  
6. Insertar la flag en el formato picoCTF correspondiente para validar el reto.

# Notas adicionales  
- Es común que el reto requiera **múltiples capas de decodificación**: Base64 → URL → HTML entities, etc.  
- Las herramientas automáticas como CyberChef facilitan mucho el proceso, ya que permiten encadenar operaciones.  
- Si el contenido parece ilegible luego de una decodificación, probar con otro tipo hasta que la salida sea coherente.  
- Estos ejercicios enseñan a reconocer patrones de codificación y evitar confundirlos con cifrado real.

# Referencias  
- Video: *Web Decode | Web exploitation | picoCTF 2024* — Canal: get__pismed  
- Publicado: 3 abril 2024  
- URL del video: http://www.youtube.com/watch?v=fKZoMYYiI80  
- Contenido accesible: http://googleusercontent.com/youtube_content/4
