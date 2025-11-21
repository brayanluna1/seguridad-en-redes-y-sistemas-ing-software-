

# Descripción

Este desafío de **criptografía** consiste en recuperar un mensaje cifrado con RSA donde el módulo `N` es demasiado grande para ser factorizado. La clave del reto es que el exponente de cifrado **E es pequeño (`E = 20`)**, lo que permite utilizar un **ataque de raíz pequeña** basado en el método de Coppersmith. El video de referencia (_PicoCTF Crack the Power_, canal COZT) muestra exactamente este procedimiento.

# Solución

1. **Obtener los valores públicos** del reto:
    
    - `N` (módulo RSA)
        
    - `E = 20` (exponente pequeño)
        
    - `C` (mensaje cifrado)
        
2. **Identificar la vulnerabilidad:**  
    Con un exponente pequeño y un mensaje `M` también pequeño, se puede aplicar el **Small Root Attack**, permitiendo calcular directamente la raíz E-ésima del ciphertext.
    
3. **Implementar el ataque con Python y `gmpy2`:**
    
    - Calcular la raíz exacta:
        
        ```
        gmpy2.iroot(C, E)
        ```
        
    - El resultado es el mensaje original `M`.
        
4. **Convertir el mensaje a texto:**  
    Transformar `M` a bytes y decodificarlo para revelar la **flag** de picoCTF.
    

# Notas adicionales

- El ataque funciona **solo** porque `M^E < N`.
    
- No es necesario factorizar el módulo.
    
- Este reto demuestra por qué en RSA **no debe usarse un exponente tan pequeño** sin relleno seguro (padding).
    
- La solución completa en el video usa una secuencia sencilla de Python, sin herramientas externas.
    

# Referencias

- Video: _PicoCTF Crack the Power_ — COZT  
    [http://googleusercontent.com/youtube_content/19](http://googleusercontent.com/youtube_content/19)