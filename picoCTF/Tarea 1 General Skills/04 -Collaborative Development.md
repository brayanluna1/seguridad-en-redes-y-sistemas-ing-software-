## Descripción
Todo el contenido del write-up debe estar dentro de este bloque.  
El reto consiste en analizar un repositorio `.git` incluido dentro del zip para encontrar partes del flag distribuidas en distintas ramas.

## Pasos

### 1. Descargar el archivo
```bash
wget https://artifacts.picoctf.net/c_titan/70/challenge.zip
```

### 2. Descomprimirlo
```bash
unzip challenge.zip
```

### 3. Entrar al directorio
```bash
cd drop-in
```

### 4. Ver ramas disponibles
```bash
git branch
```
Ramas encontradas:
```
feature/part-1
feature/part-2
feature/part-3
main
master
```

### 5. Revisar cada rama

#### feature/part-1
```bash
git checkout feature/part-1
cat flag.py
```
Salida:
```
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')
```

#### feature/part-2
```bash
git checkout feature/part-2
cat flag.py
```
Salida:
```
print("Printing the flag...")
print("m@k3s_th3_dr3@m_", end='')
```

#### feature/part-3
```bash
git checkout feature/part-3
cat flag.py
```
Salida:
```
print("Printing the flag...")
print("w0rk_7ffa0077}")
```

### 6. Flag final
```
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_7ffa0077}
```

### Notas
- Todo estaba en ramas distintas.
- El archivo `flag.py` de `main` es un señuelo.
- Hay que revisar todas las ramas en retos de Git.


