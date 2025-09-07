# Descripción
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings) without running it?
# Solución 
Primero descargué el archivo y lo ejecuté, pero no funcionó; al parecer no se puede ejecutar.  
Después, investigando, conocí `strings`, que es **un programa que extrae todas las secuencias de texto legibles** dentro de un archivo, lo cual me ayudó a descifrar lo que había. Con un `grep`, encontré la frase.
```
brayan@Nitro-Brayan:~$ wget https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings

brayan@Nitro-Brayan:~$ strings strings | grep "picoCTF"
picoCTF{5tRIng5_1T_827aee91}
```
# Notas adicionales 

# Referencias 
