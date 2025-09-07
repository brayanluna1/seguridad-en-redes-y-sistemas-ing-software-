# Descripción
Our flag printing service has started glitching!`$ nc saturn.picoctf.net 57266`

# Solución 
1. Nos conectamos al servicio usando `nc saturn.picoctf.net 51557`.

2. La salida recibida fue: `'picoCTF{gl17ch_m3_n07_' + chr(0x39) + chr(0x63) + chr(0x34) + chr(0x32) + chr(0x61) + chr(0x34) + chr(0x35) + chr(0x64) + '}'`

3. Convertimos cada `chr()` de hexadecimal a ASCII:
```
data = input("Pega la cadena aquí: ")
print("Flag:", eval(data))
```

solucion : picoCTF{gl17ch_m3_n07_bda68f75}



# Notas adicionales 
- Esta técnica de “glitching” es común en CTFs donde la salida no está en texto plano, sino codificada o fragmentada.

- Python ayuda a reconstruir la información fácilmente usando `chr()` y concatenación.
# Referencias 
