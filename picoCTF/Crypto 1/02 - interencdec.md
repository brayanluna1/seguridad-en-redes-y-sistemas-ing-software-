# Descripción
Este reto presenta una cadena codificada varias veces. El objetivo es obtener la flag en formato **picoCTF{...}** mediante un proceso de decodificación progresiva.  
El nombre *interencdec* hace referencia a una secuencia encadenada de **encode → decode → encode → decode**, lo que implica múltiples capas de codificación.

# Solución

## 1. Primera etapa – Doble decodificación Base64
El reto inicia con una cadena larga que termina en `==`, típico de Base64.

### **Paso 1 – Primera decodificación Base64**
Se toma la cadena proporcionada y se aplica una primera decodificación Base64.  
El resultado no es legible directamente: suele verse como otra cadena Base64, pero puede venir con caracteres extra, por ejemplo:

```
b'YW5vdGhlcl9iYXNlNjRfZW5jb2RlZA=='
```

La presencia del prefijo `b'...'` indica que debe limpiarse antes de continuar.

### **Paso 2 – Limpieza del resultado**
Se eliminan manualmente caracteres como:

* `b'`
* `'`
* Comillas u otros artefactos

Al limpiar, queda una cadena válida nuevamente en Base64.

### **Paso 3 – Segunda decodificación Base64**
Se realiza una segunda decodificación Base64:

```
YW5vdGhlcl9iYXNlNjRfZW5jb2RlZA==
↓ Base64 decode
another_base64_encoded
```

El resultado ya es texto legible, pero **no** es aún la flag.

---

## 2. Segunda etapa – Decodificación clásica (Cifrado César)

El texto obtenido tras la doble decodificación se identifica como un criptograma generado con un **Cifrado César**.

### **Paso 4 – Identificación del cifrado**
Se observa que el texto solo contiene letras y tiene estructura similar a palabras reales, pero desplazadas.  
Esto encaja con un **shift cipher** (rotación sobre alfabeto).

### **Paso 5 – Aplicar Cifrado César**
Se prueba un desplazamiento de 0 a 25 (por fuerza bruta) hasta obtener un texto completamente legible.

Ejemplo conceptual:

```
oruhpLfw) → shift 3 → loremIpsum
```

Al aplicar el desplazamiento correcto, se revela la flag.

---

## 3. Resultado – Flag obtenida
Tras aplicar el Cifrado César con el shift correcto, se obtiene la flag final en formato:

```
picoCTF{...}
```

(La flag exacta depende de la cadena entregada en el reto.)

# Notas adicionales
* Este reto pone en práctica la capacidad de reconocer rápidamente patrones comunes:  
  - Cadenas Base64  
  - Artefactos de impresión de Python  
  - Textos compatibles con cifrado César  
* En muchos write-ups se automatizan estos pasos con un script en Python que decodifica Base64 repetidamente y luego prueba todos los shifts.
* La estructura general del reto es:
  1. Base64 → Base64  
  2. Base64 → texto cifrado  
  3. César → flag final  

# Referencias
* Documentación Base64 – RFC 4648  
* Cifrado César – Técnicas de criptoanálisis clásico  
* Herramientas recomendadas:
  - https://www.dcode.fr/base64-decode  
  - https://www.dcode.fr/caesar-cipher  
