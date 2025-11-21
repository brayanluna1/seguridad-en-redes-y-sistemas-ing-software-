
## 📄 Descripción del Reto
Run the Python script and convert the given number from decimal to binary to get the flag.
*Download Python script*

---

## 🛠️ Solución
````
El desafío consistió en ejecutar el script de Python, el cual generaba números decimales aleatorios. El jugador debía convertir cada número a su valor binario y proporcionarlo como respuesta al script hasta que se revelara la *flag*.

### 1. Descarga del Script

Se utilizó el comando `wget` para descargar el script de Python:

**Comando y Salida:**
```bash
brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/24/convertme.py](https://artifacts.picoctf.net/c/24/convertme.py)
--2025-10-19 10:34:26--  [https://artifacts.picoctf.net/c/24/convertme.py](https://artifacts.picoctf.net/c/24/convertme.py)
[...]
Saving to: ‘convertme.py’

convertme.py        100%[================>]   1.16K  --.-KB/s    in 0s

2025-10-19 10:34:27 (230 MB/s) - ‘convertme.py’ saved [1189/1189]
````

### 2. Conversiones y Obtención de la Flag

El script requirió múltiples ejecuciones hasta que se introdujo una respuesta binaria correcta:

|**Ejecución**|**Número Decimal**|**Conversión Binaria**|**Resultado**|
|---|---|---|---|
|**1**|49|N/A (Intento fallido)|`That isn't a binary number.`|
|**2**|76|N/A (Intento fallido)|`That isn't a binary number.`|
|**3**|**63**|**111111**|¡Correcto!|

**Conversión de 63 a Binario (Verificación):**

Python

```
>>> bin(63)
'0b111111'
```

**Comandos y Salida Final:**

Bash

```
brayan@Nitro-Brayan:~$ python3 convertme.py
If 63 is in decimal base, what is it in binary base?
Answer: 0b111111
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_722f6b39}
```

## 🎉 Flag Final

`picoCTF{4ll_y0ur_b4535_722f6b39}`

---

## 💡 Notas Adicionales

- **Conversión de Bases:** El reto se centra en la habilidad de cambiar la representación de un número de base 10 (decimal) a base 2 (binario).
    
- **Uso de Python:** El intérprete de Python es la herramienta más rápida para estas conversiones usando la función integrada `bin()`.
    
- **Múltiples Intentos:** Es común en este tipo de scripts que el número decimal cambie con cada ejecución, requiriendo múltiples conversiones hasta que el número final sea el que desbloquea la _flag_.
    
- **Formato de Respuesta:** Aunque `bin(63)` produce `'0b111111'`, el script aceptó `0b111111` como una respuesta binaria válida.