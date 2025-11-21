# Descripción  
El reto **secrets** consiste en localizar una cadena de rutas ocultas dentro de una aplicación web. El objetivo es inspeccionar profundamente el código fuente de distintas páginas para encontrar directorios, archivos y referencias encadenadas que finalmente revelan la flag. El desafío enfatiza la exploración manual, la lectura de código HTML/CSS y el seguimiento de pistas ocultas entre varias rutas internas del sitio.

# Solución  
1. Inspeccionar el **código fuente** de la página principal.  
2. Observar referencias a directorios como `/vendor`, `/secret` y `/secret/assets`.  
3. Entrar a `/secret`, donde aparece el mensaje “Finally you almost found you're doing well”.  
4. Inspeccionar nuevamente el código fuente y localizar el archivo **hiddenfile.css**.  
5. Acceder a `/secret/hiddenfile.css` y encontrar en su contenido una referencia adicional hacia una ruta con **superhidden**.  
6. Intentar entrar a la ruta completa; aunque inicialmente devuelve un error **404**, retroceder un nivel revela una nueva página con el mensaje “Finally you found me but can you see me”.  
7. Abrir el código fuente de esta última página y localizar la **flag** de picoCTF.

# Notas adicionales  
- Este reto ejemplifica el uso de **arquitecturas web mal estructuradas**, donde los archivos estáticos contienen información sensible.  
- Se refuerza la importancia de revisar archivos auxiliares como `.css`, ya que pueden contener comentarios reveladores.  
- Navegar directorios manualmente sigue siendo una habilidad esencial en retos de Web Exploitation.

# Referencias  
- Video: *secrets | picoCTF 2022*  
- Canal: Rahul Singh Chauhan  
- URL del video: http://www.youtube.com/watch?v=40DYCMInk5E  
- Contenido accesible: http://googleusercontent.com/youtube_content/7
