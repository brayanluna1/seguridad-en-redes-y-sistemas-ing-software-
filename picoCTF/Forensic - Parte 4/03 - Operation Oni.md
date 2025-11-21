# Descripción
El objetivo del reto es extraer una llave SSH escondida dentro de una imagen de disco comprimida y usarla para ingresar a un servidor remoto donde se encuentra la flag. El proceso se basa en análisis forense de disco utilizando herramientas de The Sleuth Kit (mmls, fls, icat). Agradecimiento al video "picoCTF 2021 writeup [32] - Forensic - Operation Oni", que inspiró la estructura de esta solución.

# Solución
1. Se descargó y descomprimió la imagen:
   wget https://artifacts.picoctf.net/c/71/disk.img.gz
   gzip -d disk.img.gz

2. Se listaron las particiones para obtener el offset correcto:
   mmls disk.img
   - La partición raíz se encontró en el offset 206848.

3. Se listaron los archivos dentro de la partición:
   fls -o 206848 disk.img
   - Navegando entre directorios se encontró el directorio /root con:
     .ash_history
     .ssh

4. Se listaron los archivos dentro del directorio .ssh:
   fls -o 206848 disk.img 3916
   - Se identificaron los archivos:
     id_ed25519
     id_ed25519.pub

5. Se extrajo la llave privada usando icat:
   icat -o 206848 disk.img 2345 > key_file

6. Se ajustaron los permisos de la llave SSH:
   chmod 400 key_file

7. Se ingresó al servidor remoto usando la llave extraída:
   ssh -i key_file -p 58486 ctf-player@saturn.picoctf.net

8. Ya dentro del servidor se leyó la flag:
   cat flag.txt

9. Flag obtenida:
   picoCTF{k3y_5l3u7h_af277f77}

# Notas adicionales
El uso de Sleuth Kit permite navegar particiones, directorios e inodes de manera precisa para recuperar archivos borrados, ocultos o inaccesibles. Es importante usar el offset correcto al listar y extraer. Los permisos de la llave SSH deben ser estrictos para que el cliente SSH no la rechace.

# Referencias
Basado en el análisis del video "picoCTF 2021 writeup [32] - Forensic - Operation Oni" y en el uso estándar de herramientas forenses mmls, fls e icat.
