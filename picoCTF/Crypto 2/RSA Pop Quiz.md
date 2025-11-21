# Descripción
**Título del Reto:** RSA Pop Quiz  
**Plataforma/Categoría:** picoCTF, Criptografía.  
**Enunciado:** Se presenta un conjunto de preguntas interactivas sobre RSA mediante un servidor remoto. Cada pregunta evalúa conocimiento de operaciones básicas de RSA: cálculo del módulo, factorización, totiente, cifrado, descifrado y obtención de claves.  
**Objetivo:** Responder correctamente las 8 rondas para obtener la flag.  
**Mecanismo:** Conectarse al servidor, interpretar cada caso y aplicar la fórmula correcta según los valores proporcionados.

# Solución
El proceso consistió en preparar el entorno, automatizar las respuestas mediante un script y resolver cada pregunta según las propiedades del algoritmo RSA.

## Preparación del entorno (Resumen)
- Conexión tentativa vía Netcat al servidor del reto → falló por entrada inválida.  
- Intento de instalar `pwntools` desde pip → error PEP 668.  
- Instalación correcta mediante `sudo apt install python3-pwntools`.  
- Ejecución del script `rsa_solver.py` → completó automáticamente todas las rondas y obtuvo la flag.

## Desarrollo de las rondas

### **Ronda 1 — Cálculo del módulo n**
- Datos:  
  - p = 76753  
  - q = 60413  
- Pregunta: “¿Es posible calcular n?” → Sí  
- Fórmula: n = p × q  
- Resultado: **4636878989**

### **Ronda 2 — Obtención del factor q**
- Datos:  
  - p = 54269  
  - n = 5051846941  
- Pregunta: “¿Es posible calcular q?” → Sí  
- Fórmula: q = n / p  
- Resultado: **93089**

### **Ronda 3 — Factorización imposible**
- Datos:  
  - n extremadamente grande (~400 dígitos)  
  - e = 3  
- Pregunta: “¿Se pueden obtener p y q?” → No  
- Motivo: Factorizar un n de tamaño RSA real es computacionalmente inviable sin información adicional.

### **Ronda 4 — Cálculo de φ(n)**
- Datos:  
  - p = 12611  
  - q = 66347  
- Pregunta: “¿Es posible calcular el totiente?” → Sí  
- Fórmula: φ(n) = (p−1)(q−1)  
- Resultado: **836623060**

### **Ronda 5 — Cifrado (obtener c)**
- Datos:  
  - m = (entero largo)  
  - e = 3  
  - n = (n grande)  
- Pregunta: “¿Es posible cifrar?” → Sí  
- Fórmula: c = m^e mod n  
- Resultado: **25693124663...4813**

### **Ronda 6 — Descifrado imposible**
- Datos:  
  - c = (entero grande)  
  - e = 3  
  - n = (n grande)  
- Pregunta: “¿Se puede obtener m?” → No  
- Motivo: No se conoce p ni q → no se puede obtener d.

### **Ronda 7 — Cálculo de d (clave privada)**
- Datos:  
  - p = (entero gigante)  
  - q = (entero gigante)  
  - e = 65537  
- Pregunta: “¿Es posible obtener d?” → Sí  
- Fórmulas:  
  1. φ(n) = (p−1)(q−1)  
  2. d = e⁻¹ mod φ(n)  
- Resultado: **1405046269503...56729**

### **Ronda 8 — Descifrado final (obtener m)**
- Datos:  
  - p = (entero grande)  
  - c = (entero grande)  
  - e = 65537  
  - n = (entero grande)  
- Pregunta: “¿Es posible obtener m?” → Sí  
- Fórmulas:  
  1. q = n / p  
  2. φ(n) = (p−1)(q−1)  
  3. d = e⁻¹ mod φ(n)  
  4. m = c^d mod n  
- Resultado: **2183786612351...9565**

### Conversión a texto
- Decimal → Hex → ASCII  
- Resultado final: `picoCTF{wA8_th4till3aGal..ob6435DeB}`

# Notas adicionales
- El reto demuestra la diferencia entre operaciones viables (multiplicar, dividir, modular exponentiation) y operaciones imposibles (factorización sin pistas).  
- El uso de `pwntools` agiliza respuestas interactivas y evita errores humanos.  
- La conversión final de decimal a texto es clave en retos RSA de picoCTF.

# Referencias
- Documentación oficial de RSA (cálculo de claves, totiente, cifrado/descifrado).  
- Material de picoCTF sobre criptografía modular.  
- Script local `rsa_solver.py` empleado para automatizar las respuestas.
