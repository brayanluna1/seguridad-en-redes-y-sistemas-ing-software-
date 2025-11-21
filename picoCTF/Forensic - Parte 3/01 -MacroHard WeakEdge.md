# Descripción
El desafío consiste en analizar un archivo de Microsoft PowerPoint con macros (`Forensics is fun.pptm`) para localizar la bandera oculta. Aunque el archivo contiene macros, estas son un **engaño** (red herring), y la verdadera bandera se encuentra en un archivo oculto dentro de la estructura interna del PPTM. La resolución combina análisis forense de archivos Office y decodificación Base64.

# Solución
1. **Inspección inicial y macros**
   - Se verificó que el archivo contiene macros:
     ```bash
     python3 /path/to/oledump.py Forensics\ is\ fun.pptm -s 3 -v
     ```
   - Resultado: función `not_flag()` con cadena `"sorry_but_this_isn't_it"`.
   - Conclusión: las macros no contienen la flag, son un **red herring**.

2. **Descompresión del archivo**
   - Los archivos PPTM son esencialmente ZIPs, por lo que se descomprimió:
     ```bash
     unzip Forensics\ is\ fun.pptm -d forensics_unzipped
     ```

3. **Exploración de la estructura interna**
   - Se navegó a la carpeta de presentación:
     ```bash
     cd forensics_unzipped/ppt/
     ```
   - Se revisaron los archivos de slide masters:
     ```bash
     ls slideMasters
     ```
   - Se encontró un archivo llamado `hidden` que no pertenece a la estructura estándar.

4. **Extracción del contenido**
   - Se inspeccionó el archivo oculto:
     ```bash
     cat slideMasters/hidden
     ```
   - Contenido: cadena de caracteres con espacios (`Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q`).

5. **Decodificación Base64**
   - Se limpiaron los espacios y se decodificó Base64:
     ```bash
     cat slideMasters/hidden | sed 's/ //g' | base64 -d
     ```
   - Resultado: 
     ```
     picoCTF{D1d_u_kn0w_ppts_r_z1p5}
     ```

# Notas adicionales
- Este reto demuestra que los archivos Office pueden contener información escondida en su estructura interna ZIP.
- Las macros pueden distraer; siempre conviene inspeccionar el contenido real de los archivos PPTM/DOCX/XLSX.
- La bandera estaba codificada en Base64 con espacios para dificultar la lectura directa.

# Resultado final
```
picoCTF{D1d_u_kn0w_ppts_r_z1p5}
```

