# Descripción
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 7480`.

# Solución 
``` 
brayan@Nitro-Brayan:~$ nc jupiter.challenges.picoctf.org 7480 | grep -aoE 'picoCTF\{[^}]+\}'
picoCTF{digital_plumb3r_06e9d954}
``` 

# Notas adicionales 
- `-a`: trata la salida como texto aunque sea “binaria”.
- `-o`: muestra solo la parte que coincide.
- `-E`: usa regex extendidas.

# Referencias 
chatgpt