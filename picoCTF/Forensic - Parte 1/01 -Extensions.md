# Descripción
Desafío de la categoría **Forense** (*Forensics*). El objetivo es recuperar la *flag* contenida en un archivo cuya **extensión es incorrecta**. El archivo se proporciona inicialmente como `flag.txt` [00:01:13], pero la inspección forense revela que su tipo real es una imagen **PNG**.

## 💡 Concepto Clave: Falsificación de Extensión
La seguridad y el tipo real de un archivo se basan en su **firma binaria** (*Magic Bytes*), la secuencia de bytes al inicio del archivo, y no en la extensión (`.txt`, `.png`, etc.) [00:01:41].

# Solución
La solución consiste en identificar el verdadero tipo de archivo y renombrarlo con la extensión correcta para poder visualizar su contenido.

## 🐧 Solución en Entorno Linux (Web Shell)

### Paso 1: Descarga e Identificación del Tipo
Se descarga el archivo y se utiliza el comando `file` para inspeccionar la firma binaria real, ignorando la extensión visible.

| Comando | Función | Resultado Clave |
| :--- | :--- | :--- |
| `wget [URL_DEL_ARCHIVO] -O flag.txt` | Descarga el archivo al directorio de trabajo [00:01:02]. | |
| `file flag.txt` | Analiza el archivo [00:01:17]. | Revela: `flag.txt: PNG image data, ...` [00:01:22]. |

### Paso 2: Corrección y Visualización
Se renombra el archivo y se utiliza una herramienta de transferencia para verlo localmente.

```bash
# Renombra el archivo a la extensión correcta (.png).
mv flag.txt flag.png

# Transfiere la imagen al equipo local para visualizarla (comando común en web shells).
sz flag.png