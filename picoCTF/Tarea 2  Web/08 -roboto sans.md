
# Descripción  
El reto **roboto sans** se basa en identificar pistas dentro del sitio web que permitan descubrir rutas ocultas. El nombre del desafío es una referencia directa al archivo **robots.txt**, un archivo estándar utilizado para indicar a los rastreadores qué directorios o archivos no deben indexar. Dentro de este archivo se encuentra información codificada que conduce a la ubicación real de la flag.

# Solución  
1. Abrir el sitio y revisar el **código fuente** de la página principal.  
2. El código muestra un mensaje indicando que la flag no está allí y que se debe seguir buscando.  
3. Intentar acceder a directorios comunes como `/images`, `/js` y `/css` resulta en errores **403 Forbidden**.  
4. Analizar nuevamente el nombre del reto: **roboto sans**, que sugiere revisar **robots.txt**.  
5. Acceder a `/robots.txt`, donde aparece contenido aparentemente en Base64 con un carácter inválido.  
6. Copiar la cadena válida, eliminar el carácter erróneo y decodificarla.  
7. La decodificación revela el archivo **myfile.txt**.  
8. Navegar a `/myfile.txt` y obtener la **flag** de picoCTF.

# Notas adicionales  
- Este reto enseña a pensar más allá del código fuente principal y aprovechar archivos estándar poco protegidos.  
- `robots.txt` no debe incluir rutas sensibles, ya que es públicamente accesible.  
- La alteración mínima (un carácter inválido) es una técnica común para evitar decodificación directa sin análisis.

# Referencias  
- Video: *roboto sans | picoCTF 2022*  
- Canal: Rahul Singh Chauhan  
- URL del video: http://www.youtube.com/watch?v=4J-Nse2bKtc  
- Contenido accesible: http://googleusercontent.com/youtube_content/6
