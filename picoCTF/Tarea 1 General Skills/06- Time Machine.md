

# Descripción
El reto dice: *“What was I last working on? I remember writing a note to help me remember...”*  
Esto indica que la información importante fue escrita en el repositorio pero posiblemente ya no está en el último commit.  
Debemos revisar el historial o el reflog para encontrar la nota original.

# Solución

## 1. Descargar los archivos del reto
```bash
wget https://artifacts.picoctf.net/c_titan/66/challenge.zip
```

## 2. Descomprimir el archivo
```bash
unzip challenge.zip
```

Esto crea la carpeta:
```
drop-in/
```

Dentro contiene un repositorio Git.

## 3. Entrar al repositorio
```bash
cd drop-in/drop-in
```
Y luego:
```bash
cd drop-in
```

## 4. Confirmar el contenido
```bash
ls -la
```

Salida:
```
message.txt
.git/
```

El archivo `message.txt` actual NO contiene la flag.

## 5. Revisar el reflog
El reflog muestra todos los movimientos de HEAD, incluso los commits iniciales.

```bash
git reflog
```

Salida proporcionada:
```
3339c14 (HEAD -> master) HEAD@{0}: commit (initial): picoCTF{t1m3m@ch1n3_d3161c0f}
```

Esto significa que la flag estaba en el commit inicial.

## FLAG FINAL
```
picoCTF{t1m3m@ch1n3_d3161c0f}
```

# Notas adicionales
- `git reflog` es útil cuando `git log` no muestra suficiente historial.
- El reto se llama “Time Machine” porque usamos Git como una máquina del tiempo para ver estados previos.
- No hizo falta hacer `checkout`, ya que el reflog mostró directamente la flag.

# Referencias
- comandos: `git reflog`, `git log`
- documentación oficial de Git

