### Descripción

Find the flag in the Python script!

---

### Solución 🛠️

El reto se resolvió mediante la **corrección de errores de sintaxis y flujo de control** en el script `serpentine.py` para forzar la ejecución del descifrado XOR.

1. **Descarga:** Se obtuvo el script `serpentine.py`.
    
2. **Análisis:** Se observó que el script presenta un menú que **intencionalmente** no llama a la función `print_flag()`.
    
3. **Corrección de Flujo/Sintaxis:** Se modificó el código para **eliminar el bucle de menú** y **llamar directamente** a la función `print_flag()`, corrigiendo el error de sintaxis en la línea `print flag()` por `print(flag())` (o `print_flag()` en el `main`).
    

**Pasos Clave en la Terminal:**

Bash

```
brayan@Nitro-Brayan:~$ wget https://artifacts.picoctf.net/c/37/serpentine.py
brayan@Nitro-Brayan:~$ python3 serpentine.py
# El script ejecuta el menú, pero la opción 'b' falla.

brayan@Nitro-Brayan:~$ nano serpentine.py
# Se corrigen errores de sintaxis y la lógica de ejecución (como se ve en el video).

brayan@Nitro-Brayan:~$ python3 serpentine.py
/home/brayan/serpentine.py:38: SyntaxWarning: invalid escape sequence '\ '
  '''
picoCTF{7h3_r04d_l355_7r4v3l3d_8e47d128}
```

---

### Referencias 🔗

- **Técnica:** Modificación de código (Debugging y Código de Ejecución).
    
- **Base Metodológica:** Writeups/Tutoriales de picoCTF (p. ej., "PicoCTF Walkthru [68] - Serpentine").
    
- **Flag Final:** `picoCTF{7h3_r04d_l355_7r4v3l3d_8e47d128}`