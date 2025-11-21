## 📄 Descripción del Reto
Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell.
*Download runme.py Python script*

---

## 🛠️ Solución
````
El reto se resolvió siguiendo los pasos básicos para trabajar con scripts de Python en la línea de comandos: descargar el archivo y ejecutarlo con el intérprete `python3`.

### 1. Descarga del Script

Se utilizó el comando `wget` para descargar el script del artefacto de picoCTF:

```bash
brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/34/runme.py](https://artifacts.picoctf.net/c/34/runme.py)
````

**Salida de la Terminal:**

```
--2025-10-19 10:21:59--  [https://artifacts.picoctf.net/c/34/runme.py](https://artifacts.picoctf.net/c/34/runme.py)
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.26, 3.161.55.100, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: ‘runme.py’

runme.py            100%[================>]      270  --.-KB/s    in 0s

2025-10-19 10:21:59 (81.1 MB/s) - ‘runme.py’ saved [270/270]
```

### 2. Ejecución del Script

Una vez descargado, el script se ejecutó directamente usando `python3`.

Bash

```
brayan@Nitro-Brayan:~$ python3 runme.py
```

**Salida de la Terminal (Flag Obtenida):**

```
picoCTF{run_s4n1ty_run}
```

## 🎉 Flag Final

`picoCTF{run_s4n1ty_run}`

---

## 💡 Notas Adicionales

- **`wget`:** Herramienta de línea de comandos esencial para recuperar contenido de servidores web.
    
- **`python3`:** Comando utilizado para invocar el intérprete de Python versión 3 y ejecutar el script.
    
- **Simplicidad:** Este desafío forma parte de las Habilidades Generales y está diseñado para asegurar que el jugador sabe cómo descargar y ejecutar archivos de código simples.