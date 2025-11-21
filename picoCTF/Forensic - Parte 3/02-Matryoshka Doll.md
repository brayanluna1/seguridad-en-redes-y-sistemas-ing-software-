# Descripción
Este reto presenta un archivo inicial llamado `dolls.jpg`, el cual contiene múltiples capas de archivos embebidos, simulando el concepto de muñecas rusas (“matryoshkas”). El objetivo es extraer recursivamente todos los archivos ocultos dentro de la imagen usando herramientas de análisis forense como `binwalk` y `unzip`, hasta llegar al archivo final que contiene la bandera.

# Solución
1. **Identificación del archivo**
   - Se verifica el tipo de archivo:
     ```bash
     file dolls.jpg
     ```
   - Se confirma que es una imagen PNG válida.
   - Se inspecciona el contenido en busca de cadenas:
     ```bash
     strings -n 8 dolls.jpg
     ```

2. **Extracción de la primera capa**
   - Se ejecuta binwalk para extraer archivos embebidos:
     ```bash
     binwalk -e dolls.jpg
     ```
   - Dentro del directorio generado `_dolls.jpg.extracted` se encuentra:
     - `4286C.zip`
     - `base_images/`

3. **Extracción de ZIPs e imágenes anidadas**
   - Se descomprime el primer ZIP:
     ```bash
     unzip 4286C.zip -d zip_extracted
     ```
   - Dentro de `zip_extracted/base_images` se encuentra la imagen `2_c.jpg`.

4. **Repetición del proceso en cada capa**
   - Se aplica binwalk nuevamente:
     ```bash
     binwalk -e 2_c.jpg
     ```
   - Se obtiene otro ZIP (`2DD3B.zip`), que se descomprime:
     ```bash
     unzip 2DD3B.zip -d zip_extracted
     ```
   - Esto conduce a otra imagen (`3_c.jpg`), a la cual también se le aplica binwalk:
     ```bash
     binwalk -e 3_c.jpg
     ```
   - Nuevamente surge un ZIP (`1E2D6.zip`), que contiene otra imagen (`4_c.jpg`).

5. **Capa final**
   - Se analiza la última imagen:
     ```bash
     binwalk -e 4_c.jpg
     ```
   - Dentro del directorio extraído se encuentra el archivo `flag.txt`.

6. **Obtención de la bandera**
   - Se muestra el contenido del archivo final:
     ```bash
     cat flag.txt
     ```
   - La bandera obtenida es:
     ```
     picoCTF{ac0072c423ee13bfc0b166af72e25b61}
     ```

# Notas adicionales
- Este reto es un ejemplo clásico de esteganografía basada en archivos anidados.
- El uso de `binwalk -e` acelera mucho la extracción de capas.
- En ocasiones, estos retos requieren aplicar el proceso repetidamente hasta encontrar la última capa.
- Es recomendable mantener una estructura de directorios clara para no perderse entre las capas.

# Referencias
- Herramienta binwalk: https://github.com/ReFirmLabs/binwalk
- Documentación básica de comandos Linux: `file`, `strings`, `unzip`
- Plataforma picoCTF: https://picoctf.org
