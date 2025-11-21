# Descripción
El creador del repositorio escribió accidentalmente la bandera en un commit anterior, pero luego la borró.  
La pista dice: *"I accidentally wrote the flag down. Good thing I deleted it!"*  
Esto implica que debemos revisar el historial del repositorio para encontrar commits anteriores donde la flag aún existía.

# Solución

## 1. Descargar el archivo del reto
```bash
wget https://artifacts.picoctf.net/c_titan/76/challenge.zip
```

## 2. Descomprimir el archivo
```bash
unzip challenge.zip
```

Esto crea la carpeta:
```
drop-in/
```

Dentro contiene:
- Un repositorio `.git`
- Un archivo `message.txt` (modificado)
- Archivos del proyecto

## 3. Entrar al repositorio
```bash
cd drop-in/drop-in
```

## 4. Ver los commits existentes
```bash
git log
```

Salida relevante:
```
commit a6dca68e4310585eac3b5c9caf0f75967dfe972c (HEAD -> master)
    remove sensitive info

commit e720dc26a1a55405fbdf4d338d465335c439fb3e
    create flag
```

El commit más reciente dice *"remove sensitive info"*, lo que confirma que la flag fue borrada.

## 5. Cambiar al commit donde se creó la flag
```bash
git checkout e720dc26a1a55405fbdf4d338d465335c439fb3e
```

Esto coloca el repositorio en el estado anterior donde la flag todavía estaba.

## 6. Leer el archivo con la flag original
```bash
cat message.txt
```

Salida:
```
picoCTF{s@n1t1z3_7246792d}
```

## FLAG FINAL
```
picoCTF{s@n1t1z3_7246792d}
```

# Notas adicionales
- El archivo `message.txt` había sido editado en el commit más reciente, por eso mostraba “TOP SECRET”.
- El reto se resuelve revisando commits anteriores.
- Siempre revisar `git log` y luego hacer `git checkout <commit>` para ver versiones anteriores.

# Referencias
- comandos básicos de Git (`log`, `checkout`)
- documentación de picoCTF

