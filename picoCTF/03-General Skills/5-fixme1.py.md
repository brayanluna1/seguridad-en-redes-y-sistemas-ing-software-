


## Descripción
Fix the syntax error in this Python script to print the flag.
*Download Python script*

---

## Solución 🛠️
````
El script `fixme1.py` contenía al menos dos errores que impedían su ejecución. La solución fue depurar el código, corregir los errores de sintaxis e indentación, y finalmente ejecutar el script con Python 3.

### 1. Descarga del Script
Se utilizó `wget` para obtener el archivo de los artefactos de picoCTF:

**Comando y Salida:**
```bash
brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/26/fixme1.py](https://artifacts.picoctf.net/c/26/fixme1.py)
[...]
2025-10-19 10:58:02 (165 MB/s) - ‘fixme1.py’ saved [837/837]
````

### 2. Diagnóstico y Corrección de Errores

Se utilizaron múltiples ejecuciones y el editor **`nano`** para identificar y corregir los problemas:

|**Error Encontrado**|**Síntoma en la Terminal**|**Corrección Aplicada**|
|---|---|---|
|**SyntaxError**|Fallo en la función `str_xor` (asumido del código fuente).|Se completó la función `zip()` y los paréntesis.|
|**IndentationError**|`IndentationError: unexpected indent` en la línea del `print`.|Se eliminó el espacio en blanco o sangría de la línea `print(...)` para que quedara alineada a la izquierda (nivel superior).|

**Salida con Error de Indentación:**

Bash

```
brayan@Nitro-Brayan:~$ python3 fixme1.py
  File "/home/brayan/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
```

### 3. Ejecución Final

Tras corregir los errores en el editor, el script se ejecutó exitosamente.

**Comando y Flag Obtenida:**

Bash

```
brayan@Nitro-Brayan:~$ python3 fixme1.py
picoCTF{1nd3nt1ty_cr1515_09ee727a}
```

---

## Notas adicionales 💡

- **IndentationError:** En Python, la indentación es crucial. Este error resalta que una línea de código (`print`) estaba sangrada como si perteneciera a un bloque (`if`, `for`, `def`), cuando en realidad debía estar en el flujo principal del script.
    
- **XOR Encryptión:** El script utiliza la función `str_xor` para descifrar la _flag_, una técnica común en CTF. La corrección del `SyntaxError` permitió que esta función se ejecutara correctamente.
    

---

## Referencias 🔗

- **Comando `wget`:** Utilizado para descargar archivos de la web.
    
- **Comando `nano`:** Editor de texto simple en línea de comandos para la corrección de código.
    
- **`python3`:** Intérprete utilizado para ejecutar el script corregido.
    
- **Flag Final:** `picoCTF{1nd3nt1ty_cr1515_09ee727a}`