# Descripción
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 21135`, but it doesn't speak English...

# Solución 
primero descarge el texto en un archivo, 
``` 
brayan@Nitro-Brayan:~$ nc mercury.picoctf.net 21135 > out.txt
``` 
Despues lo decifre con el siguente comando que encontre en un foro raro jajajaj 
``` 
awk '{printf "%c",$1} END{print ""}' out.txt
``` 
Solucion : picoCTF{g00d_k1tty!_n1c3_k1tty!_afd5fda4}

# Notas adicionales 

# Referencias 
