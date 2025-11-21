# Descripción

El reto combina **esteganografía** y **criptografía**.  
Primero se deben extraer datos ocultos dentro de una imagen mediante análisis de capas, y luego descifrar el contenido utilizando el cifrado sugerido por el propio archivo del desafío.

# Solución

1. **Análisis esteganográfico**
    
    - Se abre la imagen del reto (`app_bash.png`) con una herramienta como **AperySolve** o **StegSolve**.
        
    - Se revisan las distintas capas (RGB, Alpha, LSB, etc.) para localizar datos ocultos.
        
2. **Extracción de información**
    
    - La herramienta detecta un archivo incrustado, usualmente llamado `encrypt.txt` o `encrypted_3.txt`.
        
    - Se extrae el contenido y se obtiene un texto cifrado ilegible.
        
3. **Identificación del cifrado**
    
    - El nombre del archivo del desafío (`app_bash`) funciona como pista principal.
        
    - Esto indica que el método de descifrado adecuado es **App‑Bash Cipher**.
        
4. **Descifrado del mensaje**
    
    - Se ingresa el texto cifrado en una herramienta o script de **App‑Bash Decoder**.
        
    - El descifrado revela la cadena final en formato de flag.
        
5. **Flag obtenida**  
    `picoCTF{app_bash_etc_etc}`
    

# Notas adicionales

- El reto enfatiza el vínculo entre esteganografía y la interpretación de pistas externas.
    
- El nombre de los archivos suele ser determinante para identificar el cifrado correcto.
    
- AperySolve y StegSolve permiten visualizar metadatos, capas y archivos incrustados.
    

# Referencias

- Herramientas de análisis: StegSolve, AperySolve.
    
- Documentación del App‑Bash Cipher para descifrado.