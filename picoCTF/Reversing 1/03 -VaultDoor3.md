# Descripción
Reto de ingeniería inversa de picoCTF donde se entrega el archivo `VaultDoor3.java`. El programa oculta la flag aplicando un “scramble” (mezcla) a la contraseña ingresada y comparando el resultado con una cadena dura embebida en el código. La flag real NO es la cadena dura, sino la contraseña que al ser mezclada por el algoritmo produce dicha cadena.

# Solución
1. Se descarga el archivo:
   ```
   wget https://jupiter.challenges.picoctf.org/static/ff2585f7afd21b81f69d2fbe37c081ae/VaultDoor3.java
   ```
2. Se analiza el código Java. El método `checkPassword()`:
   - Exige una contraseña de longitud 32.
   - Aplica un algoritmo de mezcla usando arreglos byte y posiciones alteradas.
   - Compara el resultado con la cadena dura:
     ```
     jU5t_a_sna_3lpm11g54e_u_4_m4r042
     ```
3. Para obtener la flag real se modifica temporalmente el código:
   - Se hace que imprima el buffer mezclado en lugar de regresar solo `true/false`.
   - Esto permite ver cuál es la transformación exacta.
4. Se ejecuta ingresando la cadena dura como entrada del usuario:
   ```
   picoCTF{jU5t_a_sna_3lpm11g54e_u_4_m4r042}
   ```
5. El programa imprime la versión **inversa**, es decir, la flag real:
   ```
   jU5t_a_s1mpl3_an4gr4m_4_u_e45012
   ```
6. Se prueba ingresando la flag real completa:
   ```
   picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_e45012}
   ```
7. Resultado: “Access granted.”

**Flag:**  
`picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_e45012}`

# Notas adicionales
- La cadena dura provista en el código es la versión mezclada.  
- La estrategia óptima es usar el propio algoritmo para invertir la mezcla en lugar de intentar resolverla manualmente.  
- Este reto enseña el riesgo de confiar en “seguridad por ofuscación”.

# Referencias
- Video guía mencionado en tu descripción.  
- Archivo original: `VaultDoor3.java` de picoCTF.
