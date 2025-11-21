# Descripción
Desafío de la categoría **Forense** (*Forensics*). El objetivo es recuperar la *flag* que ha sido incrustada en las secciones de datos binarios no utilizados de un archivo de imagen **JPEG** (técnica de Esteganografía básica).

## 💡 Concepto Clave: El Comando `strings`
El comando `strings` se utiliza para escanear archivos binarios y extraer secuencias de caracteres legibles, buscando contenido oculto que un visualizador normal ignora.

# Solución (Análisis de Interrupción / Proceso Incompleto)
Se documenta hasta el punto donde la ejecución se realizó correctamente antes de fallar o ser interrumpida.

## 🟢 Parte Completada y Exitosa
Se realizó la descarga del archivo y se ejecutó la extracción de cadenas.

| Comando Ejecutado | Función | Resultado |
| :--- | :--- | :--- |
| `wget [URL_DEL_ARCHIVO] -O garden.jpg` | Descarga de la imagen del desafío. | Archivo **`garden.jpg`** creado en el directorio local. |
| `strings garden.jpg` | Extracción de todas las cadenas de texto legibles. | Proceso **exitoso**, pero con una **gran cantidad de ruido** (metadatos JPEG, rutas, etc.) devuelto a la terminal. |

## 🔴 Punto de Falla/Interrupción
El proceso fue interrumpido o falló al intentar refinar la salida para aislar la *flag*.

| Comando Fallido/Pendiente | Razón del Fallo (Simulación) |
| :--- | :--- |
| `strings garden.jpg | grep -i 'pctf'` | **Fallo al Filtrar:** El usuario no ejecutó el filtro `grep` o lo hizo de forma incorrecta. **Resultado:** El usuario tiene la salida completa de `strings` pero no puede encontrar la *flag* debido a la cantidad de texto basura. |
| **Recuperación de la Flag** | **Interrupción:** El usuario interrumpió el proceso (Ctrl+C) o cerró la terminal antes de poder escanear manualmente el *output* de `strings` y encontrar la *flag*. |

## 🔑 Próximo Paso para la Solución
El usuario debe **completar el filtrado de la salida** para aislar la *flag* sin tener que buscar manualmente entre todo el ruido:

```bash
# Comando a ejecutar para completar la tarea:
strings garden.jpg | grep -i 'pctf'