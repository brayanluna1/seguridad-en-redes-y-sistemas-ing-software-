# Descripción
El reto consiste en obtener la flag oculta dentro de una imagen PNG llamada concat_v.png. Esta imagen contiene múltiples frames concatenados verticalmente, lo cual genera una altura muy grande que impide el análisis directo con herramientas esteganográficas como zsteg. El objetivo es dividir la imagen en frames pequeños y revisar cada uno para encontrar fragmentos de la bandera.

# Solución
1. Se descargó el archivo del servidor:
   wget http://mercury.picoctf.net:58537/concat_v.png

2. Se verificó el tamaño y existencia del archivo:
   ls -lh concat_v.png

3. Se intentó analizar con zsteg:
   zsteg concat_v.png
   - El resultado arrojó el error: “stack level too deep”, indicando que la imagen es demasiado grande.

4. Se revisaron las dimensiones de la imagen:
   identify concat_v.png
   - Se observó que la imagen posee una altura muy grande, debido a múltiples frames concatenados verticalmente.

5. Se procedió a cortar la imagen completa en frames individuales usando ImageMagick:
   mkdir frames
   convert concat_v.png -crop 500x500 +repage frames/frame_%04d.png

6. Con los frames generados, se analizaron individualmente:
   zsteg frames/frame_0000.png
   - Alternativamente, se buscaron textos de forma rápida:
     strings frames/*.png | grep pico

7. Al analizar los frames y concatenar los fragmentos encontrados, se reconstruye la bandera con el formato picoCTF{…}.

# Notas adicionales
El error de zsteg se debe a que no puede procesar imágenes con una altura excesiva. Cuando una imagen PNG está formada por muchas imágenes apiladas verticalmente, debe recortarse en frames antes del análisis. La búsqueda con strings es útil para localizar textos representativos de la bandera sin necesidad de un análisis visual.

# Referencias
Proceso basado en el manejo de imágenes concatenadas, uso de ImageMagick para recorte, y análisis esteganográfico mediante zsteg y strings.
