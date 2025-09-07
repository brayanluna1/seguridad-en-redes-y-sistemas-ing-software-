# Descripción
Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)

# Solución 
primero descargamos el archivo en cuestión,  para después descomprimirlo :
```
┌──(Brayan㉿Nitro-Brayan)-[~]
└─$ unzip big-zip-files.zip
```
esto nos dio muchas muchas carpetas lo que hice fue usar un grep con un -p para permime usar **Perl-compatible regular expressions (PCRE)**.
```
grep -R "picoCTF{" .
./big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```
 dando la solucion :
 picoCTF{gr3p_15_m4g1c_ef8790dc}

# Notas adicionales 

# Referencias 
