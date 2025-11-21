

# Descripción

El reto **credstuff** consiste en analizar un archivo de texto que contiene múltiples líneas con posibles credenciales. La _flag_ está oculta dentro del archivo en forma cifrada. Según el walkthrough del video (_credstuff | ROT13 | picoCTF Walkthrough || Abhay_, canal CybSec Buddy), el contenido revelado utiliza el cifrado **ROT13**, un tipo de sustitución simple que rota 13 posiciones en el alfabeto.

# Solución

1. **Buscar la línea con la flag** dentro del archivo `passwords.txt` utilizando expresiones regulares:
    
    ```
    grep -E '\{.*\}' passwords.txt
    ```
    
    Esto devuelve la cadena cifrada con el formato de flag:
    
    ```
    cvpbPGS{P7e1S_54I35_71Z3}
    ```
    
2. **Identificar el tipo de cifrado:**  
    El prefijo `cvpbPGS` corresponde a `picoCTF`, pero cifrado con **ROT13**, lo que confirma que toda la flag está convertida con el mismo método.
    
3. **Aplicar ROT13 a toda la cadena:**  
    Decodificar el texto cifrado:
    
    ```
    cvpbPGS{P7e1S_54I35_71Z3}
    ```
    
    Resultado:
    
    ```
    picoCTF{C7r1F_54V35_71M3}
    ```
    
4. **La flag final del reto es:**  
    **picoCTF{C7r1F_54V35_71M3}**
    

# Notas adicionales

- `ROT13` es un cifrado reversible aplicando el mismo proceso dos veces.
    
- `grep -E '\{.*\}'` es la forma más fiable de detectar una flag en texto cuando sigue el formato `{...}`.
    
- Este reto combina búsqueda básica en archivos + reconocimiento de cifrados clásicos.
    
- El walkthrough del video coincide exactamente con el proceso anterior.
    

# Referencias

- Video: _credstuff | ROT13 | picoCTF Walkthrough || Abhay_ — CybSec Buddy  
    [http://googleusercontent.com/youtube_content/20](http://googleusercontent.com/youtube_content/20)