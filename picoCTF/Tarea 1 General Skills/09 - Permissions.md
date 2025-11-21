# Descripción  
Este reto se centra en la escalada de privilegios en un sistema Linux: el usuario conectado tiene ciertas autorizaciones y debe descubrir cómo obtener acceso root.  
Se inicia sesión por SSH con credenciales provistas, luego se revisan los permisos del usuario y se explota una herramienta permitida (en este caso `vi`) para conseguir privilegios elevados.

# Solución  
1. Conectarse al servidor SSH con el usuario y host dados.  
2. Ejecutar:  
   ```bash
   sudo -l
   ```
   para ver qué comandos se pueden ejecutar como root.  
3. Descubrir que `vi` (o editor de texto similar) se puede ejecutar como root.  
4. Dentro de `vi`, ejecutar el comando de shell para obtener root, por ejemplo:  
   ```vi
   :!/bin/bash
   ```
5. Cambiar al directorio `/root` y listar los archivos ocultos con:  
   ```bash
   ls -la /root
   ```
6. Leer el archivo que contiene la flag.  
   Ejemplo:  
   ```bash
   cat /root/flag.txt
   ```
7. Recuperar la bandera del reto.

# Notas adicionales  
- La técnica se basa en que `vi` (o programa similar) permite suspenderse o ejecutar shell cuando se ejecuta como root.  
- Revisar siempre los permisos de `sudo -l` para detectar qué binarios se pueden usar como root.  
- A menudo en CTFs, la bandera está en `/root` o en un archivo con permisos restrictivos.  
- Esta clase de retos enseña la importancia de las “permissions” en Linux.

# Referencias  
- Writeup original: “Permissions (Writeup) | PicoCTF 2023” por Peter Muiruri. :contentReference[oaicite:0]{index=0}  
- GTFO Bins – lista de escapes y elevaciones de privilegio.  
- Documentación de `sudo`: https://www.sudo.ws/man/1.8.6/sudoers.man.html  
