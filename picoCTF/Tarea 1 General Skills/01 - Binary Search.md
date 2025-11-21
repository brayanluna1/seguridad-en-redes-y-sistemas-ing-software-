# Descripción
Este reto de picoCTF consiste en conectarse a un servidor mediante SSH donde se ejecuta un juego de búsqueda binaria.  
El servidor elige un número entre **1 y 1000**, y después de cada intento responde con:
- **Higher** si el número correcto es mayor.
- **Lower** si es menor.
- **Congratulations** cuando se acierta.

El objetivo es encontrar el número usando una estrategia eficiente (búsqueda binaria) para obtener la bandera (flag).  
El reto incluye también un archivo descargable (`challenge.zip`) que contiene el programa para analizar su funcionamiento.

# Solución
1. Conectarse al servidor remoto usando SSH:
   ```bash
   ssh -p <puerto> ctf-player@atlas.picoctf.net
   ```
2. Introducir la contraseña proporcionada por picoCTF.
3. El servidor muestra el inicio del juego:
   ```
   Welcome to the Binary Search Game!
   I'm thinking of a number between 1 and 1000.
   ```
4. Aplicar **búsqueda binaria**:
   - Se comienza por la mitad del rango (500).
   - Si dice *Higher*, se sube el rango.
   - Si dice *Lower*, se baja el rango.
   - Se repite hasta encontrar el número correcto.

5. Secuencia real que llevó a la solución:
   ```
   500 → Higher
   750 → Lower
   600 → Higher
   650 → Lower
   640 → Lower
   625 → Lower
   611 → Lower
   609 → Higher
   610 → Correct!
   ```

6. El servidor entrega la bandera:
   ```
   picoCTF{g00d_gu355_ee8225d0}
   ```

# Notas adicionales
- El juego tiene un número limitado de intentos, así que la búsqueda binaria es obligatoria.
- Si aparece “Connection refused”, solo es necesario volver a intentar con el puerto correcto.
- `challenge.zip` contiene el código del servidor para entender cómo procesa la entrada y valida los intentos.
- Cada jugador recibe un puerto distinto para la sesión SSH, asignado por picoCTF.

# Referencias
- Plataforma picoCTF  
- Concepto de búsqueda binaria  
- Archivo entregado: `challenge.zip`  
- Servidor remoto: atlas.picoctf.net
