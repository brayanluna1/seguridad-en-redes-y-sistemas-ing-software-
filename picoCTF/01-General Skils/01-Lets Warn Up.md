# Descripción 
If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?

# Solución 
#### Forma 1

use una pagina para convertirde hex a ascii

picoCTF{p}

#### Forma 2

```pyhon
	# Hexadecimal a ASCII
def hex_to_ascii(hex_string):
    # Elimina el "0x" si está presente
    hex_string = hex_string.replace("0x", "")
    # Convierte cada par de dígitos hex en un carácter ASCII
    return bytes.fromhex(hex_string).decode("ascii")
    
print(hex_to_ascii("70"))

```
# Referencias

[From Hex - CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex\('0x'\)&input=MHg3MA)