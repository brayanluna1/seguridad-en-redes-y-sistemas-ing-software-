## Descripción

Can you crack the password to get the flag?

Download the password checker here and you'll need the encrypted flag in the same directory too.

---

## Solución 🛠️

El desafío requirió **ingeniería inversa simple** (lectura de código fuente) para descifrar la contraseña que estaba codificada en **hexadecimal** dentro del script `level2.py`.

### 1. Descarga de Archivos

Se descargaron el script verificador y el archivo cifrado.

**Comandos y Salida:**

Bash

```
brayan@Nitro-Brayan:~$ wget https://artifacts.picoctf.net/c/14/level2.py
[...]
2025-10-19 15:05:22 (142 MB/s) - ‘level2.py’ saved [914/914]

brayan@Nitro-Brayan:~$ wget https://artifacts.picoctf.net/c/14/level2.flag.txt.enc
[...]
2025-10-19 15:05:32 (796 KB/s) - ‘level2.flag.txt.enc’ saved [31/31]
```

### 2. Inspección del Código y Descifrado de la Contraseña

Tras un intento fallido con una contraseña aleatoria (`xd`), se inspeccionó el código fuente de `level2.py` para encontrar la condición de la contraseña.

**Condición de Contraseña Encontrada:**

Python

```
if( user_pw == chr(0x34) + chr(0x65) + chr(0x63) + chr(0x39) ):
```

**Conversión de Hexadecimal a ASCII:**

|**Hexadecimal**|**Carácter ASCII**|
|---|---|
|`0x34`|**4**|
|`0x65`|**e**|
|`0x63`|**c**|
|`0x39`|**9**|

La contraseña correcta es: **`4ec9`**.

### 3. Ejecución Final

Se ejecutó el script con la contraseña descifrada, revelando la _flag_.

**Comando y Flag Obtenida:**

Bash

```
brayan@Nitro-Brayan:~$ python3 level2.py
Please enter correct password for flag: 4ec9
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_9701e681}
```

---

## Notas adicionales 💡

- **Encoding Oculto:** Este reto es una progresión del PW Crack 1, forzando al atacante a no solo leer el código, sino también a realizar una **decodificación de bases** (Hex a ASCII) para encontrar la clave.
    
- **Función `chr()`:** La función `chr()` de Python convierte un valor numérico (como `0x34`) a su carácter correspondiente en ASCII o Unicode.
    

---

## Referencias 🔗

- **Herramientas:** `wget`, `python3`.
    
- **Técnica:** Inspección de código fuente y decodificación Hex a ASCII.
    
- **Contraseña:** `4ec9`
    
- **Flag Final:** `picoCTF{tr45h_51ng1ng_9701e681}`