# Descripción

Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/e38f6a5b69b45d21e33cf7281d8c2531/Addadshashanammu.zip)
# Solución 
 primero descargamos el archivo
 despues descomprimimos el .zip 
 ```
 ─$ unzip Addadshashanammu.zip
 ```
despues buscamos hasta la ultima carpeta conn ayuda de tap para mayor velocidad 
para despues usar grep  para encontrar el archivo con ayuda de strings 
 ``` 
 strings fang-of-haynekhtnamet | grep picoCTF
*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_f3553887}
 ```
# Notas adicionales 


# Referencias 
