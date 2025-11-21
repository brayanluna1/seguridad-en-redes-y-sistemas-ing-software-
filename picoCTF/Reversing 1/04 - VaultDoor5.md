# Descripción
Reto de ingeniería inversa de picoCTF donde el archivo `VaultDoor5.java` aplica **dos capas de codificación** a la contraseña ingresada: primero **URL encoding** y luego **Base64 encoding**. El resultado se compara con una cadena dura (`expected`). La flag real se obtiene revirtiendo ambas codificaciones.

# Solución
1. El código convierte la contraseña así:
   - `password.getBytes()` → **URL Encode** → string con `%XX`.
   - Luego Base64 del resultado.
   - Compara con `expected`.

2. Cadena `expected`:
   ```
   JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVmJTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2JTM0JTVmJTYyJTY1JTM5JTY2JTMxJTMwJTYxJTM0
   ```

3. **Invertir el proceso**:
   - **Base64 decode** →
     ```
     %63%30%6e%76%33%72%74%31%6e%67%5f%66%72%30%6d%5f%62%61%35%65%5f%36%34%5f%62%65%39%66%31%30%61%34
     ```
   - **URL decode** →  
     ```
     c0nv3rt1ng_fr0m_ba5e_64_be9f10a4
     ```

4. Formato final de flag:
   ```
   picoCTF{c0nv3rt1ng_fr0m_ba5e_64_be9f10a4}
   ```

# Notas adicionales
- El reto enseña a revertir codificaciones encadenadas.  
- No se requiere ingeniería inversa compleja: basta con aplicar Base64 decode y luego URL decode.  
- Puede resolverse con herramientas como CyberChef, Python o el propio Java si se modifica.

# Referencias
- Archivo original `VaultDoor5.java`.  
- Ejercicio picoCTF Vault Door 5.  
- Flujo de decodificación mostrado en el video de guía.
