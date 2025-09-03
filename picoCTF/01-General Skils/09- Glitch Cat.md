# Descripción
Our flag printing service has started glitching!
Additional details will be available after launching your challenge instance.

# Solución 
1. Nos conectamos al servicio usando `nc saturn.picoctf.net 51557`.

2. La salida recibida fue: `'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'`

3. Convertimos cada `chr()` de hexadecimal a ASCII:


- `0x39` → `9`

- `0x63` → `c`

- `0x34` → `4`

- `0x32` → `2`

- `0x61` → `a`

- `0x34` → `4`

- `0x35` → `5`

- `0x64` → `d`


4. Concatenamos todo para obtener la flag final:

**SOLUCION:** `picoCTF{gl17ch_m3_n07_9c42a45d}}

# Notas adicionales 
- Esta técnica de “glitching” es común en CTFs donde la salida no está en texto plano, sino codificada o fragmentada.

- Python ayuda a reconstruir la información fácilmente usando `chr()` y concatenación.
# Referencias 
