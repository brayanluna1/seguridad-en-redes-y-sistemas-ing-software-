# Descripción  
El reto **CanYouSee** se basa en encontrar una *flag* oculta dentro de un archivo proporcionado por la plataforma. Al ser un desafío de **Forensics**, el enfoque principal consiste en analizar el archivo más allá de lo visible, explorando su estructura interna, metadatos o información embebida mediante esteganografía o herramientas de inspección.

# Solución  
1. Descargar el archivo proporcionado por el reto (generalmente una imagen).  
2. Realizar un análisis forense básico:
   - Revisar metadatos con herramientas como `exiftool`.  
   - Intentar extraer datos con `strings`.  
   - Examinar la estructura con un editor hexadecimal.  
3. Identificar contenido oculto no visible a simple vista, típicamente:
   - Texto incrustado.  
   - Comentarios ocultos.  
   - Información en capas o canales de imagen.  
4. Utilizar la herramienta adecuada (dependiendo del formato del archivo) para revelar la información oculta.  
5. Una vez encontrada, copiar la **flag** picoCTF mostrada por la herramienta o en los metadatos.

# Notas adicionales  
- Este tipo de retos suelen aplicar técnicas de **esteganografía básica** o **ocultamiento simple** dentro de archivos multimedia.  
- El video dura solo 40 segundos, lo que sugiere que la bandera estaba oculta de forma directa y se extraía rápidamente con una sola herramienta.  
- En Forensics casi siempre es útil comenzar con: `strings`, `binwalk`, `exiftool`, y algún editor hexadecimal como `xxd` o `HxD`.

# Referencias  
- Video: *CanYouSee | Forensics | picoCTF 2024*  
- Canal: get__pismed  
- URL del video: http://www.youtube.com/watch?v=gULOheSTfmk  
- Contenido accesible: http://googleusercontent.com/youtube_content/9
