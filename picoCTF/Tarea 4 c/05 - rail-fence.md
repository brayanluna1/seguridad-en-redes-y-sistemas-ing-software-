# Descripción

El desafío **rail-fence** de picoCTF 2022 utiliza el **Cifrado Rail Fence**, un método de transposición donde el texto se escribe siguiendo un patrón de zig-zag sobre varios “carriles”. Para descifrar el mensaje se debe conocer o deducir el número correcto de carriles.  
El video de referencia (_picoCTF 2022 | Cryptography | rail fence_, canal number0x01) muestra un walkthrough breve donde se ingresa el texto cifrado en una herramienta o script de Rail Fence y se prueban diferentes cantidades de carriles hasta obtener un mensaje coherente que contiene la flag.

# Solución

1. **Obtener el texto cifrado del reto** proporcionado por picoCTF.
    
2. **Abrir una herramienta de descifrado Rail Fence** (online o script local).
    
3. **Ingresar el texto cifrado** en la herramienta.
    
4. **Probar distintos valores de “número de carriles”** empezando desde 2 en adelante.
    
5. **Leer el resultado generado** hasta que aparezca un texto con sentido claro.
    
6. **Identificar la flag** dentro del texto legible obtenida al usar el número correcto de carriles.
    
7. **Copiar la flag en el formato picoCTF** tal como se muestra en la salida descifrada.
    

# Notas adicionales

- El cifrado Rail Fence no altera las letras, solo el orden: por eso probar distintos carriles revela el mensaje claro.
    
- La clave del cifrado es únicamente el **número de carriles**.
    
- El video dura 1 minuto porque el proceso es directo: ingresar texto → probar valores → encontrar la flag.
    
- No se requiere análisis adicional ni herramientas forenses.
    

# Referencias

- Video: _picoCTF 2022 | Cryptography | rail fence_ — number0x01  
    [http://googleusercontent.com/youtube_content/22](http://googleusercontent.com/youtube_content/22)