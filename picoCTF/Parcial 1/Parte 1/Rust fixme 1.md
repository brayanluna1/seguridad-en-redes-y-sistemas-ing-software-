## Descripción:
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).

# Solución
Extraer los valores hex 
Saca las cadenas hex_values del main.rs y guáralas en hex_values.txt 
Verificar el archivo hex
Configurar rust y ejecutar el código
compilar el archivo corregido
```bash
use xor_cryptor::XORCryptor;  
  
fn main () {  
// Clave para descifrado  
let key = String :: from ( "CSUCKS" ); // ¿Cómo finalizamos las declaraciones en Rust?  
  
// Valores de bandera cifrados  
let hex_values ​​= [ "41" , "30" , "20" , "63" , "4a" , "45" , "54" , "76" , "01" , "1c" , "7e" , "59" , "63" , "e1" , "61" , "25" , "7f" , "5a" , "60" , "50" , "11" , "38" , "1f" , " 3a" , "60" , "e9" , "62" , "20" , "0c" , " e6" , "50" , "d3" , "35" ];  
  
// Convertir las cadenas hexadecimales a bytes y recopilarlas en un vector  
let encrypted_buffer : Vec < u8 > = hex_values. iter ()  
. map (|&hex| u8 :: from_str_radix (hex, 16 ). unwrap ())  
. collect ();  
  
// Crear objeto de descifrado  
let res = XORCryptor:: new (&key);  
if res. is_err () {  
return ; // ¿Cómo retornamos en rust?  
}  
let xrc = res. unwrap ();  
  
// Descifrar la bandera y imprimirla  
let decrypted_buffer = xrc. decrypt_vec (encrypted_buffer);  
println! (  
"{}" , // ¿Cómo imprimimos una variable en la función println?  
String ::from_utf8_lossy (&buffer_descifrado)  
);  
}
```

Respuesta:`picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}`
## Notas

## Referencias
 