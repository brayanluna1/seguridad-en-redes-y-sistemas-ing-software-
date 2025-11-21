# Descripción
Se descarga el archivo `VaultDoorTraining.java`, el cual contiene el código fuente del reto. El programa solicita una contraseña con el formato `picoCTF{...}` y verifica el contenido interno comparándolo directamente con una cadena fija dentro del método `checkPassword`. La vulnerabilidad consiste en que la contraseña está almacenada en texto plano dentro del código, por lo que basta con leer el archivo para obtener la bandera sin necesidad de ejecutar nada.

# Solución
1. Descargar el archivo proporcionado por el reto usando `wget`.
2. Visualizar su contenido con `cat VaultDoorTraining.java`.
3. Ubicar el método `checkPassword`, donde aparece la comparación:
4. Construir la bandera siguiendo el formato requerido:
**picoCTF{w4rm1ng_Up_w1tH_jAv4_3808d338b46}**

# Notas adicionales
- Este reto demuestra por qué no debe almacenarse una contraseña directamente en el código fuente.
- Incluso en Java, el código puede verse directamente o descompilarse, haciendo inseguro este método de validación.
- Es un reto introductorio que muestra la importancia de no confiar en la seguridad por ocultamiento del código.

# Referencias
- https://play.picoctf.org/
- https://docs.oracle.com/javase/8/docs/api/
