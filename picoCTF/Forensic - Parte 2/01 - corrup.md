# Descripción
Se proporcionó un archivo llamado `mystery` desde un reto (picoCTF). El objetivo inicial fue analizar el archivo utilizando herramientas básicas del sistema: descarga, verificación de tipo, análisis hexadecimal y revisión de consistencia con herramientas estándar como `pngcheck` y `hexedit`.  
El documento describe paso a paso lo que ocurrió en la terminal durante la interacción real.

# Solución
A continuación se documentan todas las acciones realizadas en la terminal, en orden cronológico, sin alterar los comandos originales y manteniendo la fidelidad del proceso:

## 1. Descarga del archivo
Se utiliza `wget` para obtener el archivo desde el servidor del reto:

```
wget https://challenge-files.picoctf.net/c_fickle_tempest/87bdc8ce30b177d033b3d68bca4647950bb07304032861baa912ebe08701d355/mystery
```

El archivo `mystery` se descarga correctamente con un tamaño aproximado de **198 KB**, sin errores de transferencia.

## 2. Intento de instalación de herramientas
Se intentó instalar `hexeditor` y `pngcheck`:

```
sudo apt install hexeditor pngcheck
```

Resultado:  
El paquete `hexeditor` no existe en repositorios. Se procede a actualizar:

```
sudo apt update
```

Luego se reintenta instalando el paquete correcto `hexedit`:

```
sudo apt install hexedit pngcheck
```

Instalación exitosa.

## 3. Apertura del archivo con hexedit
Se revisa el archivo en formato hexadecimal:

```
hexedit mystery
```

El archivo abre correctamente para inspección manual.

## 4. Revisión con pngcheck
Se verifica si el archivo es un PNG válido:

```
pngcheck -v mystery
```

Salida importante:
- Advertencia por versión diferente de zlib.
- **ERROR: File is CORRUPTED. It seems to have suffered EOL conversion.**

Esto indica que el archivo sufrió algún tipo de alteración en saltos de línea o formato binario.

## 5. Nueva inspección en hexedit
El archivo se vuelve a abrir para búsqueda de patrones o cabeceras:

```
hexedit mystery
```

## 6. Instalación de Java (openjdk-17)
Por requerimiento del entorno o del reto, se instala OpenJDK 17:

```
sudo apt install openjdk-17-jdk
```

Se despliega una lista extensa de dependencias, se confirma con `Y`.  
La instalación finaliza sin errores.

# Notas adicionales
- El error de EOL reportado por `pngcheck` sugiere que el archivo no es realmente un PNG válido o fue modificado (intencionalmente o por transferencia).
- `hexedit` permitió visualizar contenido binario sin limitaciones.
- La instalación de Java no afectó el análisis, pero se documenta porque ocurrió durante el proceso.
- Todo el flujo corresponde directamente a lo ejecutado en la terminal, sin interpretaciones ni correcciones artificiales.

# Referencias
- Herramientas utilizadas: `wget`, `apt`, `hexedit`, `pngcheck`
- Información sobre pngcheck: https://www.libpng.org/pub/png/apps/pngcheck.html
- Documentación de paquetes en Debian/Ubuntu: https://packages.ubuntu.com/

