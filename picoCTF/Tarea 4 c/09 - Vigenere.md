# Descripción

El reto **Vigenere** utiliza el clásico **cifrado Vigenère**, un cifrado polialfabético que requiere una **clave** para descifrar el mensaje.  
El video del canal **COZT** (_PicoCTF Vigenere_, 2024) muestra cómo resolverlo usando un descifrador Vigenère en línea.

# Solución

1. **Reconocer el tipo de cifrado**  
    El desafío especifica claramente que el mensaje está cifrado con **Vigenère**, por lo que es necesario contar con la **clave** proporcionada en el mismo reto.
    
2. **Extraer los datos del desafío**
    
    - **Texto cifrado (Cipher):** Copiar el texto proporcionado en picoCTF.
        
    - **Clave (Key):** El desafío incluye la clave:
        
        ```
        cab
        ```
        
3. **Usar un descifrador Vigenère online**  
    En el video se emplea una herramienta online. El procedimiento es:
    
    - Pegar el texto cifrado.
        
    - Introducir la clave: `cab`.
        
    - Hacer clic en **Decrypt**.
        
4. **Obtener el texto plano y la flag**  
    Después de descifrar, aparece el mensaje en texto claro que incluye la flag del reto:
    
    ```
    picoCTF{don't use Vigenere Cipher}
    ```
    

# Notas adicionales

- El reto se resuelve directamente gracias a que la clave (`cab`) ya viene incluida en el material del desafío.
    
- El mensaje descifrado es una advertencia humorística sobre la debilidad del cifrado Vigenère.