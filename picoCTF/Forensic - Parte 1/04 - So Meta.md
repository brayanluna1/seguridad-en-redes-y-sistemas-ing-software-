
# Descripción
Desafío de la categoría **Forense/Esteganografía**. El objetivo es encontrar una *flag* oculta, la cual fue insertada en los **metadatos** de un archivo de imagen PNG (`pico_img.png`). Este tipo de ocultación explota campos de datos auxiliares (como EXIF o XMP) que las herramientas de visualización comunes suelen ignorar.

## 💡 Concepto Clave: Extracción de Metadatos (EXIF/XMP)
Los archivos de imagen contienen **metadatos** (datos sobre los datos) en formatos estructurados como EXIF y XMP. La herramienta **`exiftool`** está diseñada para extraer y mostrar todos estos campos, revelando la *flag* que fue incrustada en un campo como **`Artist`** o **`Creator Tool`**. 




# Solución
La solución consiste en la descarga del archivo, la instalación de la herramienta **`exiftool`** en la terminal de Linux y la inspección de la salida para encontrar el campo de texto libre que contiene la *flag*.

## 🐧 Fase 1: Preparación del Entorno y Descarga
Se prepara el entorno instalando la herramienta necesaria para el análisis forense y descargando el archivo.

| Comando Ejecutado | Propósito | Resultado Clave |
| :--- | :--- | :--- |
| `wget [URL] -O pico_img.png` | Descarga la imagen del desafío. | Archivo **`pico_img.png`** guardado. |
| `sudo apt install libimage-exiftool-perl` | Instala la herramienta forense **`exiftool`**. | Herramienta instalada con éxito tras la descarga de paquetes. |

## 🔑 Fase 2: Extracción de la Flag mediante ExifTool
Se ejecuta la herramienta sobre el archivo de imagen para obtener el listado completo de metadatos.

```bash
exiftool pico_img.png
````

Al inspeccionar la salida detallada, la _flag_ se encuentra listada en el campo de metadatos **Artist** (Artista).

|**Campo de Metadatos**|**Valor Encontrado (Flag)**|
|---|---|
|**Artist**|`picoCTF{s0_m3ta_fec06741}`|

## ✅ Flag Final

La flag del desafío es: **`picoCTF{s0_m3ta_fec06741}`**

# Notas adicionales

La advertencia de `exiftool` ("Text/EXIF chunk(s) found after PNG IDAT") indica que los datos de metadatos fueron añadidos al final del archivo PNG, una práctica que a veces es ignorada por los lectores de imágenes, pero que es visible para herramientas forenses como `exiftool`. La _flag_ se oculta deliberadamente en el campo **`Artist`** para explotar la falta de inspección profunda por parte del usuario.

# Referencias

- Herramienta utilizada: **ExifTool**
    
- Técnica: Análisis de Metadatos (EXIF/XMP Forensics)
    
- Archivo analizado: `pico_img.png`