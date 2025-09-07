# Descripción
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `abcba9f7`

Additional details will be available after launching your challenge instance.
# Solución 
Primero con ssh nos conectamos al servidor :
```
┌──(Brayan㉿Nitro-Brayan)-[~]
└─$ ssh ctf-player@venus.picoctf.net -p 55708
ctf-player@venus.picoctf.net's password:
Welcome to Ubuntu 18.04.5 LTS (GNU/Linux 5.4.0-1103-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Last login: Sun Sep  7 21:11:54 2025 from 127.0.0.1
```
Después lo que hice fue usar un ls para detectar los archivos de la consola, encontrando la primer parte de la  bandera. para después leer las instrucciones para el siguiente reto.
```
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt
picoCTF{xxsh_
```
use según las instrucciones  decía que en raíz estaba la siguiente parte de la bandera asi qeu busque ahí 
```
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ cat 2of3.flag.txt
0ut_0f_\/\/4t3r_
ctf-player@pico-chall$ cat instructions-to-3of3.txt
Lastly, ctf-player, go home... more succinctly `~`

```
y ya para terminar nos dio  la indicacionde regresar a la carpeta home  ~ asi que lo hicimos.
```
ctf-player@pico-chall$ cd ~
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt
21cac893}
```
# Notas adicionales 
en esta practica aprendimos a manejarnos de mejor manera entre las carpetas.

# Referencias 
