## Descripción:
> The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?

---

## 💻 Solución Rápida (Terminal Linux)

El error fue la **inmutabilidad** del préstamo (`&String` en lugar de `&mut String`).

1.  **Descomprimir y entrar al directorio:**
    ```bash
    tar -xzf fixme2.tar.gz
    cd fixme2
    nano src/main.rs
    ```

2.  **Correcciones Mínimas en `src/main.rs`:**

    | **Ubicación** | **CÓDIGO ORIGINAL** | **CAMBIO (Añadir `mut`)** |
    | :--- | :--- | :--- |
    | **Función `decrypt`** | `borrowed_string: &String` | `borrowed_string: &**mut** String` |
    | **Variable `party_foul`** | `let party_foul = String::from(...)` | `let **mut** party_foul = String::from(...)` |
    | **Llamada a `decrypt`** | `decrypt(..., &party_foul)` | `decrypt(..., &**mut** party_foul)` |

3.  **Compilación y Ejecución:**
    ```bash
    cargo run
    ```

---

## Bandera (Flag)

$$\text{picoCTF\{4r3\_y0u\_h4v1n5\_fun\_y31?\}}$$

## Concepto Clave

**Mutabilidad y Borrowing en Rust:** Para modificar una variable (usando `push_str`), la variable original debe ser **mutable** (`let mut`) y la referencia prestada a la función debe ser **mutable** (`&mut`).