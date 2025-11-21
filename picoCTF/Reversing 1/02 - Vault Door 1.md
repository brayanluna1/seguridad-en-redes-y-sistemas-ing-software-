# Descripción
Se proporciona el archivo `VaultDoor1.java`, el cual contiene el código fuente del reto. El programa solicita una contraseña con el formato `picoCTF{...}` y luego extrae únicamente la parte interna para compararla carácter por carácter mediante una serie de condiciones explícitas en el método `checkPassword`. La contraseña no está directamente escrita como una cadena completa, sino distribuida mediante comparaciones individuales de cada posición.

# Solución
1. Descargar el archivo con `wget` y visualizarlo con `cat VaultDoor1.java`.
2. Analizar el método `checkPassword`, el cual especifica la longitud (32 caracteres) y luego define cada letra del password según su índice.
3. Reconstruir la contraseña colocando cada carácter en su posición correspondiente:

   - 0 = d  
   - 1 = 3  
   - 2 = 5  
   - 3 = c  
   - 4 = r  
   - 5 = 4  
   - 6 = m  
   - 7 = b  
   - 8 = l  
   - 9 = 3  
   - 10 = _  
   - 11 = t  
   - 12 = H  
   - 13 = 3  
   - 14 = _  
   - 15 = c  
   - 16 = H  
   - 17 = 4  
   - 18 = r  
   - 19 = 4  
   - 20 = c  
   - 21 = T  
   - 22 = 3  
   - 23 = r  
   - 24 = 5  
   - 25 = _  
   - 26 = 7  
   - 27 = 5  
   - 28 = 0  
   - 29 = 9  
   - 30 = 2  
   - 31 = e  

   Contraseña interna completa:
   **d35cr4mbl3_tH3_cH4r4cT3r5_75092e**

4. Construir la bandera final con el formato requerido:
   **picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_75092e}**

# Notas adicionales
- Este reto demuestra una técnica común: ocultar la contraseña distribuyéndola entre comparaciones individuales.
- Aunque más "creativo" que simplemente escribir la contraseña en el código, sigue siendo completamente reversible.
- Este patrón es típico en retos de ingeniería inversa básicos.

# Referencias
- https://play.picoctf.org/
- Documentación oficial de Java (Scanner, Strings, charAt)
