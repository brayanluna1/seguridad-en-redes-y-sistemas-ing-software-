# Descripción
**Título del Reto:** b00tl3gRSA3  
**Plataforma/Categoría:** picoCTF, Criptografía (RSA no estándar).  
**Enunciado:** El servidor entrega los parámetros públicos RSA **C**, **N** y **E**, pero la descriptografía tradicional falla.  
**Problema:** El módulo **N no está compuesto solo por dos primos (p y q)**, sino por **varios factores primos**, lo que invalida la fórmula clásica de RSA.  
**Objetivo:** Calcular correctamente **φ(N)** usando **todos los factores primos** de N, obtener el exponente privado **D** y descifrar el mensaje.

# Solución
El joven sigue el procedimiento estándar inicial, pero al fallar la descriptografía clásica entiende que se trata de un RSA con múltiples primos. El reto gira en torno a obtener **φ(N)** para recomputar **D**.

## 1. Obtención de los parámetros
Se conecta vía netcat al servidor del reto y recibe:  
- **C:** Texto cifrado  
- **N:** Módulo RSA  
- **E:** Exponente público  


## 2. Identificación del problema
La primera descriptografía que intenta produce texto ilegible (“gibberish”).  


La pista del reto confirma que **N tiene más de dos factores** → no se puede usar la fórmula clásica:

\[
\phi(N) = (p-1)(q-1)
\]

Para RSA multiprimo, la fórmula general es:

\[
\phi(N)=\prod_{i}(p_i - 1)
\]

Esto es indispensable para calcular el exponente privado:

\[
D \equiv E^{-1} \pmod{\phi(N)}
\]

## 3. Factorización y cálculo de φ(N)
Como N es grande y tiene múltiples primos, se usa un servicio de factorización en línea.  


Pasos seguidos:
- Ingresa **N** en la herramienta de factorización.  
  
- La herramienta encuentra **todos los factores primos** de N.  
- Automáticamente calcula **φ(N)** usando la fórmula multiprimo.  


## 4. Desencriptación final
Una vez calculado φ(N), se procede a la descriptografía correcta.

Pasos:
- Copia el φ(N) calculado.  
- ntroduce **C**, **N**, **E** y **φ(N)** en una herramienta RSA.  
  
- La herramienta calcula **D = E^{-1} mod φ(N)**.  
- Se realiza:  
M = C^D \pmod N

 
El resultado es el mensaje original en texto claro, que contiene la flag del reto.  


### Flag obtenida:
`picoCTF{too_many_factors}`

# Notas adicionales
- Este reto introduce el concepto de **RSA multiprimo**, variante donde N tiene más de dos factores.  
- RSA multiprimo es inseguro si se utilizan primos demasiado pequeños o si existen herramientas que pueden factorizar N rápidamente.  
- La clave del reto es **no usar la fórmula clásica del totiente**.  
- Calcular φ(N) correctamente garantiza el cálculo de D, que es la pieza crítica de RSA.

# Referencias
- Documentación de RSA multiprimo.  
- Calculadoras RSA con soporte para totiente multiprimo.  
- Servicios de factorización de enteros utilizados en desafíos CTF.
