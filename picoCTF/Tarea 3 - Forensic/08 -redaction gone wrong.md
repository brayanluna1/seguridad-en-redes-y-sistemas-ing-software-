# Descripción
El desafío presenta un informe donde información sensible fue “redactada”, pero la censura se realizó de manera incorrecta. En lugar de eliminar el texto, simplemente se cubrió con un bloque/capa de color. El objetivo es recuperar el contenido real que se encuentra debajo de la supuesta redacción.

# Solución
1. Se descarga el archivo del informe proporcionado en el reto.
2. Al abrir el documento, se observa que las áreas “censuradas” no eliminan el texto: únicamente lo tapan mediante una caja negra o una capa de relleno.
3. Se selecciona el texto oculto con el cursor y se copia.
4. Se pega el texto copiado en un editor de texto simple, revelando la información que fue mal redactada.
5. El texto recuperado contiene la flag final del desafío.
6. La flag obtenida es: **picoctf{can_you_see_me_fully}**

# Notas adicionales
Este tipo de error sucede cuando se realiza redacción visual sin eliminar el contenido subyacente. Herramientas como select/copy o inspección del contenido permiten recuperar fácilmente información que se creía protegida.

# Referencias
- Video original: “pico2022 redaction gone wrong” — Martin Carlisle  
  URL: http://www.youtube.com/watch?v=XnMG16XtNbg
- Fuente del contenido en bruto: http://googleusercontent.com/youtube_content/15
