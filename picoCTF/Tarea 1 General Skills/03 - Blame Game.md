# Descripción
Se trabajó con el archivo `challenge.zip` procedente de picoCTF.  
El objetivo es descargar el reto, descomprimirlo, revisar su contenido y analizar archivos (incluyendo posibles repositorios Git) para localizar el flag típico de picoCTF.

# Solución
## 1. Descargar el archivo del reto
wget https://artifacts.picoctf.net/c_titan/156/challenge.zip

## 2. Descomprimir el archivo
unzip challenge.zip

## 3. Listar el contenido descomprimido
ls -la

## 4. Si existe un repositorio Git, entrar a la carpeta
cd repo/

## 5. Ver historial de commits
git log

## 6. Ver quién modificó cada línea de un archivo
git blame archivo

## 7. Mostrar una versión pasada del archivo
git show <hash>:archivo

## 8. Buscar directamente el flag dentro de los archivos extraídos
grep -R "picoCTF" .

# Notas adicionales
- Si `unzip` solo muestra “Archive: challenge.zip”, el archivo puede ya estar descomprimido o contener pocos archivos.  
- Muchos retos tipo “Blame Game” ocultan el flag en commits antiguos.  
- El flag siempre tiene el formato:  
  picoCTF{...}

# Referencias
https://medium.com/@technolifts/picoctf-blame-game-writeup-4849f20116b9
