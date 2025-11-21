# Descripción
En este reto se proporciona una imagen de disco comprimida. El objetivo es analizar la estructura de particiones y el sistema de archivos utilizando herramientas de **The Sleuth Kit** para identificar y recuperar archivos relevantes, incluyendo la flag.

# Solución 

## 1. Descarga y preparación del entorno
Iniciamos con un directorio limpio:

```bash
rm -rf *
ls
```

Se descarga la imagen comprimida:

```bash
wget https://artifacts.picoctf.net/c/138/disk.flag.img.gz
```

Se descomprime:

```bash
gzip -d disk.flag.img.gz
```

Archivo resultante:

* **disk.flag.img**

---

## 2. Análisis de particiones con `mmls`

```bash
mmls disk.flag.img
```

Salida relevante:

```
Offset Sector  |  Description
-------------------------------------
001: 0–2047      Unallocated
002: 2048–206847 Linux (0x83)
003: 206848–360447 Linux Swap
004: 360448–614399 Linux (0x83)
```

Se centra en la **segunda partición Linux** (offset 2048) y especialmente en la **tercera partición Linux** (offset 360448), donde se encuentran los archivos sospechosos.

---

## 3. Inspección del sistema de archivos con `fsstat`

```bash
fsstat -o 2048 disk.flag.img
```

Confirmación:

* Sistema de archivos: **ext4**
* Inodos válidos: del 1 al 25585
* Punto de montaje: `/mnt/boot`

---

## 4. Listado de archivos de la partición (offset 2048)

```bash
fls -i raw -f ext4 -o 2048 -r disk.flag.img
```

Resultados: Archivos normales del sistema (`boot`, `kernel`, `extlinux`, etc.)

---

## 5. Buscar archivos sospechosos en la partición oculta (offset 360448)

```bash
fls -i raw -f ext4 -o 360448 -r disk.flag.img | grep flag
```

Archivos identificados:

| Inodo | Nombre       |
| ----- | ------------ |
| 2082  | flag.txt     |
| 2371  | flag.uni.txt |

---

## 6. Extracción de archivos con `icat`

### 6.1. Extraer `flag.txt`

```bash
icat -i raw -f ext4 -o 360448 disk.flag.img 2082 > flag.txt
```

Contenido:

```bash
cat flag.txt
```

Resultado:

```
3.449677            13.056403
```

(No contiene la flag.)

### 6.2. Extraer `flag.uni.txt`

```bash
icat -i raw -f ext4 -o 360448 disk.flag.img 2371 > flag.uni.txt
```

Ver contenido:

```bash
cat flag.uni.txt
```

Resultado:

```
picoCTF{by73_5urf3r_2f22df38}
```

---

## 7. Flag encontrada

```
picoCTF{by73_5urf3r_2f22df38}
```

---

# Notas adicionales

* `fls` sirve para **listar** archivos y directorios, NO para extraer.  
* Para extraer archivos, se debe usar `icat`.  
* Identificar correctamente **offsets y particiones** es clave en retos forenses.  
* Revisar todas las particiones Linux ayuda a no pasar por alto archivos ocultos.  
* Este reto refuerza el manejo de **TSK** y comprensión de **inodos/ext4**.

# Referencias

* [The Sleuth Kit Documentation](https://www.sleuthkit.org/sleuthkit/docs.php)  
* [CTFtime – Sleuthkit Apprentice](https://ctftime.org/task/138)  
* [Medium – PicoCTF Write-up](https://medium.com/@atigamli/picoctf-sleuthkit-apprentice-writeup)
