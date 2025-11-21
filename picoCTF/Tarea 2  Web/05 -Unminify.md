# Descripción  
El reto **Unminify** se enfoca en analizar código JavaScript minificado dentro de una página web. El objetivo es restaurar el código a un formato legible (*unminify*), identificar su funcionamiento real y encontrar la flag oculta. El desafío pertenece a la categoría **Web Exploitation**, donde el competidor debe inspeccionar archivos del lado del cliente para descubrir información sensible escondida mediante ofuscación.

# Solución  
1. Abrir la página del reto y localizar el archivo JavaScript minificado referenciado en el HTML.  
2. Copiar el contenido minificado y usar una herramienta de *unminify/prettify*, como:  
   - beautifier.io  
   - jsbeautifier.org  
   - DevTools → pestaña Sources → botón “Pretty Print”.  
3. Analizar el código formateado para identificar funciones sospechosas, condicionales o cadenas codificadas.  
4. Localizar la parte del script donde se arma o devuelve la flag.  
5. Extraer la flag directamente del código o replicar la lógica en consola para obtenerla.

# Notas adicionales  
- La minificación NO es un método de seguridad; solo reduce tamaño y ofusca superficialmente.  
- Todo el código JS enviado al cliente es accesible y puede revertirse fácilmente.  
- Este reto es ideal para aprender a leer scripts minificados y reconocer estructuras comunes de ofuscación simple.  
- Cualquier herramienta de formateo es válida: el proceso es completamente manual y no requiere explotación avanzada.

# Referencias  
- Video: *Unminify | Web Exploitation | picoCTF 2024* — Canal: get__pismed  
- Publicado: 7 abril 2024  
- URL del video: http://www.youtube.com/watch?v=Mo4aQXsYoU8  
- Contenido accesible: http://googleusercontent.com/youtube_content/3
