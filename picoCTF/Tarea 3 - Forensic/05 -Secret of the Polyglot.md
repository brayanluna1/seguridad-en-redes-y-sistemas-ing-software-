# Descripción
El desafío consiste en analizar un archivo “políglota”, es decir, un archivo que es válido simultáneamente para dos formatos diferentes. Este tipo de archivo suele esconder información en una de sus “caras” (por ejemplo, una imagen que también contiene un ZIP incrustado). El objetivo es identificar la estructura dual y extraer el contenido oculto para recuperar la flag.

# Solución
1. Se identifica que el archivo proporcionado es un archivo políglota, lo cual permite que se interprete como más de un tipo de archivo válido.
2. Se inspecciona el archivo con herramientas forenses o mediante un editor hexadecimal para localizar la sección correspondiente al segundo formato incrustado.
3. Una vez localizada esa sección, se extrae el contenido (por ejemplo, un ZIP oculto dentro de una imagen).
4. Se abre el contenido extraído y se localiza el archivo interno que contiene la flag del desafío.
5. Se lee dicho archivo para obtener la flag final.

# Notas adicionales
Los archivos políglotas suelen construirse alineando cuidadosamente los encabezados y estructuras de dos formatos distintos. Este tipo de retos requiere familiaridad con firmas de archivo, offsets y modos de extracción manual.

# Referencias
- Video original: Secret of the Polyglot | Forensics | picoCTF 2024 — get__pismed  
  URL: http://www.youtube.com/watch?v=hVDNbN1AXZw
- Fuente del contenido en bruto: http://googleusercontent.com/youtube_content/13
