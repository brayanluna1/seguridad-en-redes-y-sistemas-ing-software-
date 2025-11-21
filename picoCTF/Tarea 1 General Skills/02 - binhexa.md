# Descripción
Este reto de picoCTF presenta una serie de operaciones binarias que deben realizarse en un orden específico.  
El jugador recibe **dos números binarios** y debe aplicar operaciones lógicas, aritméticas y desplazamientos de bits.  
Cada respuesta correcta permite avanzar hasta obtener un resultado final en **hexadecimal**, el cual revela la bandera del reto.

Números en el reto:

- **Binary Number 1:** 11011110  
- **Binary Number 2:** 11110011  

El objetivo es completar las 6 preguntas aplicando correctamente cada operación.

# Solución

### **Pregunta 1/6 – Operación ‘|’ (OR bitwise)**
```
11011110
11110011
----------
11111111
```
**Resultado:** `11111111` ✔️  

---

### **Pregunta 2/6 – Operación ‘>>’ (right shift)**
Desplazar Binary Number 2 (**11110011**) a la derecha 1 bit:

```
11110011 >> 1 = 01111001
```

**Resultado:** `01111001` ✔️  

---

### **Pregunta 3/6 – Operación ‘&’ (AND bitwise)**
```
11011110
11110011
----------
11010010
```

**Resultado:** `11010010` ✔️  

---

### **Pregunta 4/6 – Operación ‘*’ (multiplicación binaria)**
```
11011110 * 11110011 = 1101001010111010
```

**Resultado:** `1101001010111010` ✔️  

---

### **Pregunta 5/6 – Operación ‘+’ (suma binaria)**
 ```
11011110
+11110011
-----------
111010001
```

**Resultado:** `111010001` ✔️  

---

### **Pregunta 6/6 – Operación ‘<<’ (left shift)**
Desplazar Binary Number 1 (**11011110**) a la izquierda 1 bit:

```
11011110 << 1 = 110111100
```

(Primero se ingresó `10111100` incorrectamente, luego `110111100` ✔️)

**Resultado final en binario:** `110111100`

---

## **Conversión a Hexadecimal**

Se agrupa el binario en grupos de 4 bits:

```
Binary: 0001 1011 1100
Hex:      1    B    C
```

**Resultado hexadecimal final:** `1BC`

---

### **Flag**
Ingresando `1bc` (en minúsculas también funciona), el servidor responde:

```
picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_675602ae}
```

# Notas adicionales
- Las operaciones bitwise se aplican bit a bit; es útil revisar tablas de verdad de AND/OR.
- Para las operaciones de shifts, recuerda que:
  - `>>` elimina bits a la derecha.
  - `<<` agrega ceros a la derecha.
- La multiplicación binaria funciona igual que la decimal pero con bits.
- El reto permite corregir respuestas hasta avanzar.
- El formato hexadecimal no distingue entre mayúsculas y minúsculas para este problema.

# Referencias
- Tablas de verdad AND / OR  
- Operaciones bitwise  
- Conversión de binario a hexadecimal  
- Plataforma picoCTF
