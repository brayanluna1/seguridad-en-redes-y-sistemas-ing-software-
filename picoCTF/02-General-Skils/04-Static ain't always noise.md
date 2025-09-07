# Descripción
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/static)? This [BASH script](https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/ltdis.sh) might help!

# Solución 
 primero descarge el archivo que tenia el codigo bienario
 ```
  wget https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/static
   ```
  despues descargue el scrip 
```
 wget https://mercury.picoctf.net/static/e9dd71b5d11023873b8abe99cdb45551/ltdis.sh
```
  ejecute el scrip :
```
chmod +x ltdis.sh
./ltdis.sh static
brayan@Nitro-Brayan:~$ grep picoCTF static.ltdis.strings.txt
   1020 picoCTF{d15a5m_t34s3r_ae0b3ef2}
```
Solucion : picoCTF{d15a5m_t34s3r_ae0b3ef2}
# Notas adicionales 

# Referencias 