



## Descripción
Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag in the same directory too.

---

## Solución 🛠️
````
El reto no requirió fuerza bruta, sino **ingeniería inversa simple** (lectura del código fuente) para encontrar la contraseña codificada que el script utilizaba para descifrar el archivo `level1.flag.txt.enc`.

### 1. Descarga de Archivos
Se descargaron tanto el script verificador (`level1.py`) como el archivo cifrado (`level1.flag.txt.enc`).

**Comandos y Salida:**
```bash
brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/12/level1.py](https://artifacts.picoctf.net/c/12/level1.py)
[...]
2025-10-19 14:55:23 (88.0 MB/s) - ‘level1.py’ saved [876/876]

brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/12/level1.flag.txt.enc](https://artifacts.picoctf.net/c/12/level1.flag.txt.enc)
[...]
2025-10-19 14:56:49 (7.95 MB/s) - ‘level1.flag.txt.enc’ saved [30/30]
````

### 2. Diagnóstico del Error Inicial

El primer intento de ejecución falló porque faltaba el archivo cifrado (`FileNotFoundError`). Este error se resolvió al descargar `level1.flag.txt.enc`.

### 3. Inspección del Código y Obtención de la Contraseña

Tras fallar con contraseñas comunes (`xd`, `password`), se inspeccionó el código fuente de `level1.py` usando `cat`.

**Comando y Fragmento Clave del Código:**

Bash

```
brayan@Nitro-Brayan:~$ cat level1.py
[...]
def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "8713"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
[...]
```

La línea `if( user_pw == "8713"):` reveló la contraseña estática: **`8713`**.

### 4. Ejecución Final

Se ejecutó el script con la contraseña correcta para obtener la _flag_.

**Comando y Flag Obtenida:**

Bash

```
brayan@Nitro-Brayan:~$ python3 level1.py
Please enter correct password for flag: 8713
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_1b2fd683}
```

---

## Notas adicionales 💡

- **CTF vs. Realidad:** En la vida real, las contraseñas nunca están codificadas en el código de verificación. En CTF, esto es una técnica para que el jugador sepa inspeccionar el código en lugar de recurrir a la fuerza bruta inmediatamente.
    
- **XOR Cifrado:** El script utiliza la función `str_xor` para descifrar la _flag_, una forma simple de cifrado de bloque.
    

---

## Referencias 🔗

- **Herramienta:** `python3` para la ejecución del script.
    
- **Técnica:** Inspección de código fuente (`cat`).
    
- **Contraseña:** `8713`
    
- **Flag Final:** `picoCTF{545h_r1ng1ng_1b2fd683}`