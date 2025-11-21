# Descripción
**Título del Reto:** La cifra de  
**Plataforma/Categoría:** picoGym (picoCTF), Criptografía .  
**Enunciado:** "I'm decipher in an old book can you figure out what it says" (Estoy descifrando en un libro antiguo, ¿puedes averiguar qué dice?) .  
**Mecanismo:** El desafío requiere conectarse a un portal Netcat para recibir el texto cifrado .  
**Pista Clave:** El título “La cifra de” sugiere que el método de cifrado corresponde al Cifrado Vigenère (Vigenere Cipher) .  
**Objetivo:** Descifrar el texto para obtener la flag final.

# Solución
La resolución se basa en identificar correctamente el cifrado y emplear una herramienta capaz de descifrarlo incluso sin conocer la clave inicial.

1. **Obtención del texto cifrado:**  
   El texto recibido por el portal Netcat se copia directamente desde la terminal .

2. **Identificación del cifrado:**  
   Se usa la herramienta *Boxentriq Cipher Identifier* para analizar el texto cifrado .  
   Esta confirma que se trata de un **Vigenère Cipher** .

3. **Auto-Solve sin clave:**  
   En lugar de intentar deducir la clave manualmente, se utiliza la opción **Auto solve without key** del decodificador Vigenère de Boxentriq .

4. **Deducción de la clave probable:**  
   La herramienta arroja múltiples claves posibles, y muchas contienen combinaciones de las letras **F, G, A y L** .  
   Esto apunta a que la clave más probable es **FLAG** }.

5. **Descifrado final:**  
   Se ingresa la clave **FLAG** en el decodificador Vigenère y se selecciona “decode” .  
   El texto resultante revela el mensaje:  
   **bellasso or vigenere cipher** .

6. **Ingreso de la flag:**  
   La flag obtenida se introduce en el panel de picoCTF para completar el reto .

# Notas adicionales
- El título del reto es el indicio principal para reconocer que el cifrado es Vigenère.  
- Boxentriq facilita el proceso permitiendo resolver el cifrado incluso sin clave.  
- La clave “FLAG” se identifica por la repetición de patrones en las claves sugeridas.

# Referencias
- Herramienta Boxentriq Cipher Identifier (utilizada en el procedimiento).  
- Portal Netcat provisto por picoCTF para la obtención del texto cifrado.
