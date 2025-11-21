# Descripción  
El reto presenta un shell modificado llamado **Special (TM)**, un “Spell Checked Interface for Affecting Linux”, que supuestamente corrige ortografía automáticamente.  
En realidad, este shell reemplaza cualquier comando por su versión “bien escrita y capitalizada”, lo cual **rompe el uso normal del terminal**.  
El objetivo es encontrar una forma de ejecutar comandos sin que Special los modifique, para así acceder al contenido del sistema y obtener la flag.

# Solución  
1. Conectarse al servidor con las credenciales provistas:  
   ```bash
   ssh -p 53584 ctf-player@saturn.picoctf.net
   ```
2. Al entrar, cualquier comando escrito es autocorregido y convertido a una palabra capitalizada:  
   - `ls` → `Is` (y falla)  
   Esto hace que no se pueda ejecutar ningún comando normal.

3. Para saltarse Special, se puede usar **expansión de parámetros de bash**, porque *Special no la modifica*.  
   Por ejemplo:  
   ```bash
   ${parameter?ls}
   ```
   Este truco NO ejecuta `ls`, pero demuestra que el shell no modifica la sintaxis `${...}`.

4. El writeup sugiere usar una expansión que permita ejecutar un comando al asignar un parámetro:  
   ```bash
   ${parameter=cat < blargh/flag.txt}
   ```
   Aunque la parte de `<` puede fallar, el servidor igualmente revela la flag al intentar resolver la expansión.

5. Al introducir ese comando, aparece:  
   ```
   picoCTF{5p311ch3ck_15_7h3_w0r57_6a2763f6}
   ```
   Esa es la bandera del reto.

6. Después de obtenerla, el servidor cierra la conexión automáticamente:
   ```
   Connection to saturn.picoctf.net closed by remote host.
   ```

# Notas adicionales  
- Special no modifica expresiones de expansión `${...}`, por lo que esta es la vía para romper la “autocorrección”.  
- El reto enseña a aprovechar características internas de bash para ejecutar comandos indirectos.  
- La flag se encuentra dentro de la carpeta `blargh`, pero no es necesario navegarla: el truco de expansión ya la revela.  
- Este tipo de problemas muestra cómo shells “seguros” pueden romperse mediante mecanismos estándar del propio lenguaje.

# Referencias  
- Writeup: https://josephkimiri.github.io/posts/Special/  
- Documentación de bash parameter expansion: https://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html  
- Reto original en picoCTF (Special)
