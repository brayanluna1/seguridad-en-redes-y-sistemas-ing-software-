# Descripción
El video muestra cómo resolver el desafío "Information" de la categoría de Informática Forense (Forensics) en picoCTF 2021. La pista indica que la flag está oculta en un archivo JPG que fue modificado en secreto.

# Solución
1. Se descarga el archivo JPG proporcionado por el reto.
2. Se analizan los metadatos del archivo utilizando la herramienta `exiftool`.
3. Dentro de los metadatos se identifica un campo inusual llamado **License**, que contiene una cadena larga alfanumérica.
4. Se sospecha que dicha cadena está codificada en Base64.
5. Se extrae el valor de License utilizando `sed` para eliminar la etiqueta “License”.
6. La cadena limpia se pasa a `base64 -d` para decodificarla.
7. Al decodificarla aparece la flag del desafío, que revela el mensaje: **"the metadata is modified"**.

# Notas adicionales
El punto clave del reto es revisar los metadatos EXIF del archivo, ya que ahí se encuentra la cadena Base64 que contiene la flag oculta.

# Referencias
- Video original: picoCTF 2021 Information — Martin Carlisle  
  URL: http://www.youtube.com/watch?v=uG42AMp0XHU
- Fuente del contenido en bruto: http://googleusercontent.com/youtube_content/10
