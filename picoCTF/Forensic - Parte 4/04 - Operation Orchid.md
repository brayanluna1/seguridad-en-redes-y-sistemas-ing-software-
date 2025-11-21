# Reto
Operation Orchid

# Descripción
El objetivo del reto es extraer la bandera oculta dentro de una imagen de disco o archivo comprimido que contiene un sistema de archivos con archivos cifrados. El flujo combina análisis forense de particiones con extracción y descifrado de archivos. Referencias de inspiración: CTFtime y Medium ([1],[2]).

# Archivos y entorno inicial
- Archivo proporcionado: por rellenar
- Tamaño: por rellenar
- Entorno: Linux local o shell de picoCTF, recomendado trabajar en /tmp
- Herramientas usadas: `file`, `mmls`, `fls`, `icat`, `strings`, `openssl`, etc.

# Solución
1. Inspección inicial del archivo:
   ```bash
   file nombre_del_archivo
```

- Confirmé que era una imagen de disco tipo Linux.
    
- Si venía comprimido:
    

```bash
gunzip archivo.gz
```

- Verifiqué que el archivo descomprimido estuviera presente.
    

2. Analizar particiones con mmls:
    
    ```bash
    mmls nombre_imagen.img
    ```
    
    - Resultado ejemplo:
        
        ```
        000: Meta      0000000000   …
        001: Unallocated …
        002: 0000002048   … 100M Linux (0x83)
        003: 000206848   … 100M Linux swap (0x82)
        004: 000411648   … 199M Linux (0x83)
        ```
        
    - Se eligió la partición más grande y tipo Linux para explorar.
        
3. Listar archivos con fls:
    
    ```bash
    fls -o <offset> nombre_imagen.img
    ```
    
    - Navegué por los directorios listados.
        
    - Encontré en `/root/` archivos como `.ash_history` y un archivo sospechoso `flag.txt.enc`.
        
4. Extraer el archivo sospechoso con icat:
    
    ```bash
    icat -o <offset> nombre_imagen.img <inode> > flag.txt.enc
    ```
    
    - `<inode>` corresponde al inode del archivo obtenido con fls.
        
    - Verifiqué que `flag.txt.enc` estuviera en el sistema local.
        
5. Analizar e interpretar el archivo cifrado:
    
    ```bash
    file flag.txt.enc
    strings -t d flag.txt.enc | grep -i openssl
    ```
    
    - Se detectó que estaba cifrado con AES-256 + salt.
        
    - Se identificó la clave en `.ash_history`: `unbreakablepassword1234567`.
        
    
    ```bash
    openssl aes256 -d -salt -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
    ```
    
    - Obtuve el archivo `flag.txt` descifrado.
        
6. Lectura de la bandera:
    
    ```bash
    cat flag.txt
    ```
    
    - Flag encontrada:
        
        ```
        picoCTF{h4un71ng_p457_5113beab}
        ```
        

# Conclusiones

- El reto combina análisis de discos, particiones y archivos cifrados.
    
- Herramientas clave: SleuthKit (`mmls`, `fls`, `icat`), `strings`, `openssl`.
    
- Revisar archivos de historial del sistema (como `.ash_history`) permite encontrar claves y pistas de cifrado.
    
- Práctica esencial: identificar particiones, navegar el sistema de archivos, extraer archivos por inode y descifrar.
    

# Referencias

