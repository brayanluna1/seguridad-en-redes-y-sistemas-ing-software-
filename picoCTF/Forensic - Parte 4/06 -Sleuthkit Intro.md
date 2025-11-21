# Descripción
En este reto se proporciona una imagen de disco comprimida. El objetivo es analizar la estructura de particiones utilizando herramientas de **The Sleuth Kit** y determinar el tamaño de la partición Linux en sectores. Una vez identificado, se debe enviar la respuesta a un servicio remoto para obtener la flag.

# Solución 

## 1. Descarga y preparación del entorno
Iniciamos con un directorio limpio y descargamos la imagen:

```bash
wget https://artifacts.picoctf.net/c/164/disk.img.gz
```

Verificamos que el archivo se haya descargado correctamente:

```
Length: 29714372 (28M) [application/octet-stream]
Saving to: ‘disk.img.gz’
disk.img.gz 100%[================>] 28.34M
```

Se descomprime la imagen:

```bash
gzip -d disk.img.gz
```

Archivo resultante:

* **disk.img**

---

## 2. Análisis de particiones con `mmls`

```bash
mmls disk.img
```

Salida:

```
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```

La partición Linux comienza en el sector **2048** y termina en **2047999**, con un tamaño total de **202752 sectores**.

---

## 3. Envío de la respuesta al servicio remoto

Con la información obtenida, se conecta al servidor remoto para responder la pregunta:

```bash
nc saturn.picoctf.net 53065
```

Entrada solicitada:

```
What is the size of the Linux partition in the given disk image?
```

Se responde con el tamaño en sectores:

```
202752
```

---

## 4. Flag obtenida

```
picoCTF{mm15_f7w!}
```

# Notas adicionales

* `mmls` permite inspeccionar particiones y obtener **offsets y tamaños** en sectores.  
* La partición Linux identificada es la única relevante en este reto.  
* No fue necesario explorar el sistema de archivos ni extraer archivos; solo se debía calcular el tamaño.  
* Este reto sirve como práctica inicial en forense de discos con Sleuth Kit y comprensión de tablas de particiones.

# Referencias

* [The Sleuth Kit Documentation](https://www.sleuthkit.org/sleuthkit/docs.php)  
* [CTFtime – Sleuthkit Beginner](https://ctftime.org/task/164)  
* [picoCTF Official Write-ups](https://picoctf.org/)  
