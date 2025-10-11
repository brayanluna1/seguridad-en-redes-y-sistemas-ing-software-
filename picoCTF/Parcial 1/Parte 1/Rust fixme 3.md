
## Descripción:
> Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!

---

##  Solución Rápida (Terminal Linux)

El error de compilación se debe a operaciones con punteros crudos (`std::slice::from_raw_parts`) que **no estaban envueltas en un bloque `unsafe`**.

1.  **Preparación:**
    ```bash
    tar -xzf fixme3.tar.gz
    cd fixme3
    nano src/main.rs
    ```

2.  **Corrección Única en `src/main.rs`:**

    * **Acción:** Descomentar las líneas `// unsafe {` y `// }` para envolver el código que maneja `decrypted_ptr` y `decrypted_len`.

    * **Ubicación (alrededor de la línea 18):**

        ```rust
        // This is where unsafe rust comes in...
        unsafe { // <-- DESCOMENTAR
            // Decrypt the flag operations
            let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);

            // Creating a pointer...
            let decrypted_ptr = decrypted_buffer.as_ptr();
            let decrypted_len = decrypted_buffer.len();

            // Unsafe operation: calling an unsafe function...
            let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);
            
            borrowed_string.push_str(&String::from_utf8_lossy(decrypted_slice));
        } // <-- DESCOMENTAR
        ```

3.  **Compilación y Ejecución:**
    ```bash
    cargo run
    ```

---

## ✅ Bandera (Flag)

$$\text{picoCTF\{4r3\_y0u\_h4v1n5\_fun\_y31?\_n0w\_w1th\_uns4f3\_f3f98c8c\}}$$

##  Concepto Clave

**`unsafe` Rust:** Se utiliza para operaciones que el compilador no puede garantizar que sean seguras (como la desreferencia de punteros crudos). Es una barrera que indica que el programador asume la responsabilidad de la seguridad de la memoria en ese bloque.