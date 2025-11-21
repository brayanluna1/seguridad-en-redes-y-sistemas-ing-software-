# Descripción

El reto consiste en descifrar un mensaje codificado como una lista de números enteros.  
Cada número debe ser reducido utilizando **módulo 37**, ya que el alfabeto del cifrado incluye:

- 26 letras mayúsculas
    
- 10 dígitos
    
- 1 carácter especial (`_`)
    

Posteriormente, cada valor reducido se traduce a su carácter correspondiente para obtener el mensaje final.

# Solución

1. **Obtención del archivo y visualización del contenido**
    
    - `wget https://artifacts.picoctf.net/c/129/message.txt`
        
        - Descarga correcta (86 bytes).
            
    - `cat message.txt`
        
        - Se obtuvo la lista cifrada:  
            `350 63 353 198 114 369 346 184 202 322 94 235 114 110 185 188 225 212 366 374 261 213`
            
2. **Aplicación del módulo 37 (script en Python)**  
    Se implementó un script para reducir cada número:
    
    ```python
    cifrado = [350, 63, 353, 198, 114, 369, 346, 184, 202, 322, 94, 235, 114, 110, 185, 188, 225, 212, 366, 374, 261, 213]
    reducido = [n % 37 for n in cifrado]
    for num in reducido:
        print(num)
    ```
    
    **Salida del script:**  
    `17, 26, 20, 13, 3, 36, 13, 36, 17, 26, 20, 13, 3, 36, 0, 3, 3, 27, 33, 4, 2, 28`
    
3. **Mapeo de caracteres según el sistema del reto**
    
    - `0–25` → `A–Z`
        
    - `26–35` → `0–9`
        
    - `36` → `_`
        
    
    Traducción completa:
    
    - 17 → R
        
    - 26 → 0
        
    - 20 → U
        
    - 13 → N
        
    - 3 → D
        
    - 36 → _
        
    - 13 → N
        
    - 36 → _
        
    - 17 → R
        
    - 26 → 0
        
    - 20 → U
        
    - 13 → N
        
    - 3 → D
        
    - 36 → _
        
    - 0 → A
        
    - 3 → D
        
    - 3 → D
        
    - 27 → 1
        
    - 33 → 7
        
    - 4 → E
        
    - 2 → C
        
    - 28 → 2
        
4. **Resultado final**  
    El mensaje descifrado es:  
    **R0UND N R0UND ADD17EC2**
    

# Notas adicionales

- Este reto es una introducción al uso de módulos no standard como 37.
    
- La estructura del cifrado también se usa en variantes posteriores del reto.
    

# Referencias

- Documentación de PicoCTF acerca de cifrados por módulo.
    
- Esquema de mapeo oficial para _basic-mod1_.