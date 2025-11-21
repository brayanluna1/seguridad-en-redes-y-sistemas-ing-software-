# Descripción
El objetivo de este desafío era obtener la flag contenida dentro de una imagen de disco comprimida. Para esto se proporcionó un archivo .img.gz que debía descomprimirse para poder analizar su contenido. El enfoque utilizado fue realizar una búsqueda directa de cadenas legibles dentro de la imagen descomprimida.

# Solución
1. Se descargó el archivo de la imagen comprimida con:
   wget https://mercury.picoctf.net/static/2f998eee12730cf5766624681212a441/dds1-alpine.flag.img.gz

2. Una vez descargado, se descomprimió utilizando:
   gzip -d dds1-alpine.flag.img.gz
   - Esto generó el archivo dds1-alpine.flag.img.

3. Con la imagen ya descomprimida, se realizó una búsqueda de cadenas que contuvieran la palabra “pico”, típica de las flags de picoCTF:
   strings dds1-alpine.flag.img | grep pico

4. La flag apareció directamente dentro del resultado del comando anterior, sin necesidad de utilizar análisis de particiones o herramientas adicionales.

# Notas adicionales
Este reto no requirió herramientas avanzadas como SleuthKit, ya que la flag estaba accesible mediante una simple búsqueda con strings. Es importante ejecutar el comando sobre la imagen descomprimida, ya que los archivos .gz no pueden ser leídos directamente por strings.

# Referencias
Proceso realizado mediante descarga del archivo, descompresión y búsqueda manual de cadenas dentro de la imagen de disco utilizando strings.
