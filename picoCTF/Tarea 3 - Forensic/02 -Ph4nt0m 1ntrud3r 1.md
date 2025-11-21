# Descripción  
El reto **Ph4nt0m 1ntrud3r 1** presenta un escenario donde el participante debe identificar a un “intruso fantasma” mediante el análisis de artefactos digitales. El desafío sugiere la exploración de rastros ocultos, archivos sospechosos o comportamientos anómalos dentro del material proporcionado por picoCTF.

# Solución  
1. Descargar el archivo o conjunto de archivos entregados por el reto.  
2. Realizar análisis inicial del contenido:
   - Si es un archivo de logs, revisar entradas extrañas o modificaciones sospechosas.  
   - Si es una imagen o archivo binario, inspeccionar con `strings`, `exiftool`, `binwalk` o un editor hexadecimal.  
   - Si es tráfico de red, abrir el `.pcap` en Wireshark y revisar conexiones o paquetes anómalos.  
3. Identificar elementos ocultos que pudieran corresponder al “intruso fantasma”:
   - Texto oculto, rutas internas, archivos disfrazados o metadatos manipulados.  
   - Mensajes incrustados o segmentos de datos fuera de lo habitual.  
4. Seguir rastros internos que lleven a la ubicación final de la *flag*.  
5. Extraer y copiar la **flag** picoCTF encontrada en el archivo o dentro de los datos analizados.

# Notas adicionales  
- Por la temática del reto, puede implicar técnicas forenses como esteganografía simple, análisis de logs o búsqueda de artefactos de intrusión.  
- El título “Intruder” es un indicio de que el flujo lógico es seguir pistas anómalas dentro del archivo.  
- El video dura 2:13, lo que indica que el método de extracción es directo una vez identificada la pista correcta.

# Referencias  
- Video: *Pico CTF 2025 - Ph4nt0m 1ntrud3r 1*  
- Canal: SHIVANI  
- URL del video: http://www.youtube.com/watch?v=liUEfsro0kU  
- Contenido accesible: http://googleusercontent.com/youtube_content/11
