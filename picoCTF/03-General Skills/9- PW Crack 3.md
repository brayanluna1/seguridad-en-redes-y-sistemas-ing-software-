


## Descripción
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/18/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/18/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/18/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script




## Solución 🛠️

El reto se resolvió mediante un **ataque de diccionario dirigido** (o _brute-force_ dirigido) contra el hash MD5 de la contraseña correcta.

1. **Ingeniería Inversa:** Se identificó que el script utiliza la función **MD5** para hashear las contraseñas y que la contraseña correcta es una de 7 posibles.
    
2. **Modificación de Script:** Se modificó `level3.py` para reemplazar la función `input()` con un bucle que prueba las 7 contraseñas (obtenidas de una fuente externa como un archivo **`potential_passwords.txt`**).
    
3. **Ataque Dirigido:** El script automatizado probó cada clave, hasheó la clave, y la comparó con el `level3.hash.bin`. La clave que coincidió se usó para el descifrado XOR final.
    

**Salida Final (Resultado del Ataque Dirigido):**

```
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_6f98a49f}
```

---

## Notas adicionales 💡

- La contraseña tiene una doble función: **verificación** (hash MD5) y **descifrado** (llave XOR).
    
- El reto enseña el concepto de ataque dirigido cuando el espacio de claves es muy pequeño.
    

---

## Referencias 🔗

- **Técnica:** Ataque de Diccionario Dirigido sobre MD5.
    
- **Flag Final:** `picoCTF{m45h_fl1ng1ng_6f98a49f}`