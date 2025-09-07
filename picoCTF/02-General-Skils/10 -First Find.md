# Descripción
#### Description

Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/501/files.zip)
# Solución 
Primero descargamos el archivo, para después descomprimir el archivo, 
```
wget https://artifacts.picoctf.net/c/501/files.zip
unzip files.zip
```
después con ayuda del comando find nos ayudara a buscar el archivo de manera mas rápida y directa sin tener que esta en carpeta por capeta utilizando ls .
```
find . -type f -name "uber-secret.txt"
./adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
```
al final utilizamos cat con la ruta de la carpeta en cuestión, para conocer la bandera :
```
┌──(Brayan㉿Nitro-Brayan)-[~/files]
└─$ cat ./adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt
picoCTF{f1nd_15_f457_ab443fd1}
```
Solucion : picoCTF{f1nd_15_f457_ab443fd1}
# Notas adicionales 

# Referencias 
