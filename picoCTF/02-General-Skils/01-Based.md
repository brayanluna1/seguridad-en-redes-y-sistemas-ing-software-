# Descripción
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 29956`.

# Solución 
- Primero me fijé en los números a descifrar que daba. El primero fue muy fácil, era binario; me percaté por los ceros y unos.

- En la siguiente, primero pensé que sería ASCII, pero investigué y vi que el ASCII no tiene caracteres interesantes en los números superiores al 127, así que averigüé y esos números estaban en octal.

- Después seguí y me dio una gran línea de números, los cuales tenían letras como “f” y demás. Entonces me di cuenta de que estaba en hexadecimal.

```
binario= input ("dame los datos en bianerio ")
caracteres = binario.split()
texto = ''.join(chr(int(byte, 2)) for byte in caracteres)
print(texto)

valores_ascii = input("Dame los octales")
caracteres = valores_ascii.split()
texto = ''.join(chr(int(valor,8)) for valor in caracteres)
print(texto)

hex_string = input("Dame los hexadecimales ")
texto = bytes.fromhex(hex_string).decode("utf-8")
print(texto)
```
Termine usando python para resolverlo.
Solución : picoCTF{learning_about_converting_values_b375bb16}
# Notas adicionales 

# Referencias 