# Reto  
INSPECT HTML — picoCTF

# Descripción  
Este reto consiste en inspeccionar el código fuente HTML de una página web para encontrar una flag oculta. Generalmente se encuentra dentro de comentarios HTML, etiquetas no visibles, o scripts incrustados.  
El video mostrado es extremadamente corto (33 s) y no contiene explicación hablada; solo muestra de forma visual que la flag está en el HTML.

# Solución  
1. Abrir la página del reto en el navegador.  
2. Clic derecho → **Inspeccionar** (o presionar **Ctrl+U** para ver el código fuente).  
3. Buscar dentro de:  
   - Comentarios `<!-- -->`  
   - Etiquetas ocultas `<p style="display:none">`  
   - Scripts `<script>`  
4. La flag aparece directamente en el HTML sin ningún cifrado.  
5. Copiar la flag y enviarla como respuesta en picoCTF.

# Notas adicionales  
- Este tipo de retos pertenece a la categoría **Web Exploitation** de picoCTF.  
- Generalmente son los retos más sencillos: basta con mirar lo que no se ve en la interfaz normal.  
- No se requiere usar herramientas avanzadas como BurpSuite, curl o análisis de tráfico.  
- Útil activar “Buscar” (**Ctrl+F**) con palabras como `pico`, `flag`, `{`, `}`.

# Referencias  
- Video base: *SOLVING PICOCTF # INSPECT HTML #ctf #picoctf #cybersecurity* — DigiSuraksha Parhari Foundation  
- Fecha de publicación: 12 abril 2024  
- URL del video: http://www.youtube.com/watch?v=En1yYqCeDkM  
- Contenido accesible: http://googleusercontent.com/youtube_content/0
