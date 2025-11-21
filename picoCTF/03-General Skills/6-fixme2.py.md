## Descripción
Fix the syntax error in the Python script to print the flag.
*Download Python script*

---

## Solución 🛠️
````
El script `fixme2.py` fallaba debido a un error de sintaxis común en Python: usar el operador de asignación (`=`) dentro de una estructura condicional (`if`), donde se esperaba el operador de comparación (`==`).

### 1. Descarga del Script
Se utilizó `wget` para obtener el archivo de los artefactos de picoCTF:

**Comando y Salida:**
```bash
brayan@Nitro-Brayan:~$ wget [https://artifacts.picoctf.net/c/6/fixme2.py](https://artifacts.picoctf.net/c/6/fixme2.py)
--2025-10-19 11:12:09--  [https://artifacts.picoctf.net/c/6/fixme2.py](https://artifacts.picoctf.net/c/6/fixme2.py)
[...]
2025-10-19 11:12:10 (233 MB/s) - ‘fixme2.py’ saved [1029/1029]
````

### 2. Diagnóstico y Corrección del SyntaxError

Se ejecutó el script con `python3`, revelando inmediatamente el error de sintaxis y proporcionando una pista útil:

**Diagnóstico del Error:**

Bash

```
brayan@Nitro-Brayan:~$ python3 fixme2.py
  File "/home/brayan/fixme2.py", line 22
    if flag = "":
        ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```

Corrección:

El error se encontraba en la línea 22. En lugar de usar el operador de asignación (=), se necesitaba el operador de comparación (==).

1. Se abrió el archivo con `nano fixme2.py`.
    
2. Se cambió la línea de **`if flag = "":`** a **`if flag == "":`**.
    
3. Se guardó el archivo.
    

### 3. Ejecución Final

El script corregido se ejecutó sin errores, revelando la flag.

**Comando y Flag Obtenida:**

Bash

```
brayan@Nitro-Brayan:~$ python3 fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
```

---

## Notas adicionales 💡

- **Asignación vs. Comparación:** Este reto enseña una regla fundamental de Python (y muchos otros lenguajes):
    
    - **`=`** se usa para asignar un valor a una variable.
        
    - **`==`** se usa para comparar si dos valores son iguales (igualdad).
        
- **Pistas del Intérprete:** El intérprete de Python 3 fue muy útil al sugerir directamente `==` o `:=` (el operador _walrus_) como posibles correcciones, acelerando la resolución.
    

---

## Referencias 🔗

- **Comando `wget`:** Descarga de archivos del servidor.
    
- **Comando `nano`:** Utilizado para editar el código fuente y aplicar la corrección.
    
- **Error Corregido:** Reemplazo de `=` por `==`.
    
- **Flag Final:** `picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}`