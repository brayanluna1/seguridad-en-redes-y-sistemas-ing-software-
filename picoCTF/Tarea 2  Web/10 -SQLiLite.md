# Descripción  
El reto **SQLiLite** consiste en explotar una vulnerabilidad de **Inyección SQL (SQLi)** en una pantalla de inicio de sesión web. La página vulnerable construye dinámicamente consultas SQL usando entradas del usuario sin sanitización, lo que permite evadir la autenticación y acceder a la flag de picoCTF. Este desafío se centra en comprender la lógica SQL subyacente y cómo manipularla con un *payload* adecuado.

# Solución  
1. Inspeccionar la página de inicio de sesión y entender la consulta SQL subyacente:  
   ```
   SELECT * FROM users WHERE name = 'user' AND password = 'password'
   ```
2. Identificar que el formulario no valida correctamente la entrada del usuario.  
3. Preparar un *payload* de Inyección SQL para el campo de usuario:
   ```
   admin' OR 1=1 --
   ```
   - `OR 1=1` fuerza que la condición `WHERE` sea siempre verdadera.  
   - `--` comenta el resto de la consulta, ignorando la verificación de contraseña.  
4. Ingresar el *payload* en el campo de usuario y dejar el campo de contraseña vacío.  
5. Hacer clic en "Login" y observar que la autenticación se elude exitosamente.  
6. Ver la **flag** de picoCTF en la página de éxito y confirmar su presencia inspeccionando el código fuente.

# Notas adicionales  
- Este reto ejemplifica la importancia de **sanitizar entradas de usuario** en consultas SQL.  
- La técnica utilizada es una **SQL Injection clásica**, muy común en aplicaciones web mal protegidas.  
- Aunque la flag aparece directamente tras el login, siempre es buena práctica revisar el código fuente para confirmar la exposición de la información.  

# Referencias  
- Video: *SQLiLite | picoCTF 2022*  
- Canal: Rahul Singh Chauhan  
- URL del video: http://www.youtube.com/watch?v=FNVx9hCSwTY  
- Contenido accesible: http://googleusercontent.com/youtube_content/8
