 


# Descripción  
El reto consiste en descubrir cómo se automatizan tareas en servidores Linux y encontrar el flag oculto dentro del sistema.  
Al conectarse vía SSH al servidor provisto por picoCTF, se muestra un entorno limitado donde algunos directorios no se pueden acceder.  
La clave del reto es revisar las tareas programadas del sistema, ya que los desafíos relacionados con automatización suelen esconder la información en archivos de configuración de cron.

# Solución  
1. Conectarse al servidor remoto usando el usuario, host y puerto del reto:  
   ```bash
   ssh picoplayer@saturn.picoctf.net -p 54075
   ```

2. Intentar explorar el sistema de archivos:  
   ```bash
   ls -a
   cd /
   ls -la
   ```
   El directorio `/challenge` existe pero no tiene permisos para el usuario.

3. Consultar el archivo de tareas programadas del sistema:  
   ```bash
   cat /etc/crontab
   ```

4. Dentro de este archivo aparece directamente el flag:  
   ```
   # picoCTF{Sch3DUL7NG_T45K3_L1NUX_1d781160}
   ```

5. Ese es el resultado final del reto.

# Notas adicionales  
- No es necesario acceder a `/challenge`; los permisos están intencionalmente bloqueados.  
- No se requiere escalar privilegios.  
- En los retos relacionados con “cron” o “schedule”, siempre conviene revisar `/etc/crontab` o `/etc/cron.*`.  
- La estructura minimalista del contenedor es normal en picoCTF.

# Referencias  
- https://man7.org/linux/man-pages/man5/crontab.5.html  
- https://ubuntu.com/server/docs/security-automatic-updates  
- https://picoctf.org/
