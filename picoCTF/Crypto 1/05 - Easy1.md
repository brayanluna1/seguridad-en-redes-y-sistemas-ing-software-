# Descripción
El reto proporciona tres elementos:  
1. **Encrypted Flag** (texto cifrado)  
2. **Key** (clave para descifrar)  
3. **Table** (tabla de apoyo)  

La tabla y la clave sugieren que el método usado no es un one‑time pad real, sino un **Cifrado Vigenère**.  
El objetivo es descifrar la bandera utilizando la clave proporcionada y obtener el texto plano para formatearlo como **picoCTF{...}** en mayúsculas.

# Solución
1. Se identifica que la tabla usada corresponde al **Cifrado Vigenère** al comparar su estructura alfabética.  
2. Se abre una herramienta online de descifrado Vigenère.  
3. Se copia el **ciphertext** proporcionado en el campo correspondiente.  
4. Se copia la **key** dada dentro del reto en el campo de clave.  
5. Se ejecuta la opción **Decode**.  
6. La herramienta revela el texto descifrado: **CRYPTO IS FUN**.  
7. Se construye la flag final en el formato requerido:  
   **picoCTF{CRYPTO IS FUN}**.  
8. Se envía para completar el desafío.

# Notas adicionales
* El Cifrado Vigenère usa una clave repetida y una tabla alfabética, por lo que es común que los retos proporcionen ambas.  
* Aunque se menciona “one‑time pad”, este reto NO implementa un OTP real.  
* La flag debe ir **en mayúsculas** para que la plataforma la acepte.  
* Cualquier herramienta Vigenère funciona siempre que permita ingresar clave y texto cifrado.

# Referencias
* Cifrado Vigenère – documentación y explicación general.  
* Herramienta usada: https://www.dcode.fr/vigenere-cipher  
* Plataforma picoCTF – sección de criptografía.
