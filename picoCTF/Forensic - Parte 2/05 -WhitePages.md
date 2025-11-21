# Descripción
Este reto presenta un archivo aparentemente vacío llamado `whitepages.txt`. Sin embargo, al analizarlo a nivel de bytes, se revela que contiene dos tipos distintos de espacios invisibles: **ASCII SPACE (0x20)** y **EM SPACE Unicode (0xE2 80 83)**. Estos caracteres se utilizan para representar bits binarios. El objetivo es mapear cada tipo de espacio a un bit (0 o 1), reconstruir los datos binarios ocultos, y decodificar el mensaje final que contiene la bandera.

# Solución
1. **Inspección inicial del archivo**
   - Se utiliza `xxd` para examinar el contenido del archivo a nivel hexadecimal:
     ```bash
     xxd -g 1 whitepages.txt
     ```
   - Se detectan dos bytes recurrentes:
     - `20`  → ASCII SPACE
     - `e2 80 83` → EM SPACE
   - Esto confirma la presencia de información esteganográfica basada en espacios invisibles.

2. **Asignación de valores binarios**
   - Se utiliza la convención estándar para este reto:
     - EM SPACE (`e2 80 83`) → **0**
     - ASCII SPACE (`20`) → **1**

3. **Script de decodificación**
   - Se emplea un script en Python encargado de reemplazar los espacios por su valor binario correspondiente, filtrar solo 0 y 1, convertirlos a bytes y decodificar el resultado:
     ```python
     #!/usr/bin/env python3
     import base64

     EM = b'\xe2\x80\x83'
     SP = b'\x20'

     with open("whitepages.txt", "rb") as f:
         data = f.read()

     bits = (
         data
         .replace(EM, b'0')
         .replace(SP, b'1')
     )

     bits = bytes([b for b in bits if b in (48, 49)])
     bits = bits.decode()

     bits = bits[: len(bits) - (len(bits) % 8) ]

     decoded_bytes = bytes(
         int(bits[i:i+8], 2)
         for i in range(0, len(bits), 8)
     )

     print("=== TEXTO DECODIFICADO ===")
     try:
         text = decoded_bytes.decode()
         print(text)
     except:
         print(decoded_bytes)
         text = ""

     try:
         print("\n=== SI ES BASE64, AQUÍ EL RESULTADO ===")
         flag = base64.b64decode(text).decode()
         print(flag)
     except:
         pass
     ```

4. **Interpretación de la salida**
   - La primera salida del script corresponde al texto oculto, generalmente codificado en Base64.
   - La segunda salida, si aplica, es la bandera final decodificada que sigue el formato:
     ```
     picoCTF{...}
     ```

# Notas adicionales
- Este reto es un excelente ejercicio de esteganografía basada en caracteres invisibles.
- La clave está en detectar correctamente los dos tipos de espacios y mapearlos a binario.
- Asegurar que el número de bits sea múltiplo de 8 es indispensable para reconstruir bytes válidos.
- Si la decodificación inicial no es legible, intentar Base64 suele resolverlo.

# Referencias
- Esteganografía con caracteres Unicode invisibles.
- Documentación de picoCTF Forensics.
- Herramientas utilizadas: `xxd`, Python 3.
