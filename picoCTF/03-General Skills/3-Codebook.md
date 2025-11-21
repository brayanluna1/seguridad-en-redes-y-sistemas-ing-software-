
## 📄 Descripción del Reto
Run the Python script `code.py` in the same directory as `codebook.txt`.
*Download code.py*
*Download codebook.txt*

---

## 🛠️ Solución
````
El reto se resolvió asegurando que los dos archivos necesarios (`code.py` y `codebook.txt`) estuvieran en el mismo directorio de trabajo, y luego ejecutando el script de Python para que este procesara el archivo de datos y revelara la flag.

### 1. Descarga de Archivos
Se utilizó el comando `wget` para descargar ambos archivos de los artefactos de picoCTF.

**Descarga de `code.py`:**
```bash
brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/1/code.py](https://artifacts.picoctf.net/c/1/code.py)
--2025-10-19 10:28:16--  [https://artifacts.picoctf.net/c/1/code.py](https://artifacts.picoctf.net/c/1/code.py)
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.64, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: ‘code.py’

code.py             100%[================>]   1.25K  --.-KB/s    in 0s

2025-10-19 10:28:17 (225 MB/s) - ‘code.py’ saved [1278/1278]
````

**Descarga de `codebook.txt`:**

Bash

```
brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/1/codebook.txt](https://artifacts.picoctf.net/c/1/codebook.txt)
--2025-10-19 10:28:25--  [https://artifacts.picoctf.net/c/1/codebook.txt](https://artifacts.picoctf.net/c/1/codebook.txt)
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.26, 3.161.55.64, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.26|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: ‘codebook.txt’

codebook.txt        100%[================>]       27  --.-KB/s    in 0s

2025-10-19 10:28:26 (949 KB/s) - ‘codebook.txt’ saved [27/27]
```

### 2. Ejecución del Script

Se ejecutó el script con `python3`. El script leyó los datos de `codebook.txt` (que contiene la clave de descifrado) y reveló la flag.

Bash

```
brayan@Nitro-Brayan:~$ python3 code.py
```

**Salida Real de la Terminal (Flag Obtenida):**

```
picoCTF{c0d3b00k_455157_d9aa2df2}
```

## 🎉 Flag Final

`picoCTF{c0d3b00k_455157_d9aa2df2}`

# Notas adicionales 

# Referencias 