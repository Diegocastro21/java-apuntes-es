# Escape De Secuencias En Literals
Los literales de cadena y caracteres proporcionan un mecanismo de escape que permite expresar códigos de
caracteres que de otro modo no estarían permitidos en el literal.
Una secuencia de escape consiste en un carácter de barra invertida (\) seguido de uno o más caracteres.
Las mismas secuencias son válidas tanto en caracteres como en literales de cadena.

El conjunto completo de secuencias de escape es el siguiente:

| Secuencia De Escape | Significado                                            |
|---------------------|--------------------------------------------------------|
| `\\`                | Denota un carácter de barra invertida `(\)`            |
| `\'`                | Denota un carácter de una sola comilla `(')`           |
| `\"`                | Denota un carácter double-quote `(")`                  |
| `\n`                | Denota un carácter de alimentación de línea `(LF)`     |
| `\r`                | Denota un carácter de retorno de carruaje (CR)         |
| `\t`                | Denota un carácter de tabulación horizontal (HT)       |
| `\f`                | Denota un carácter de fuente de formulario (FF)        |
| `\b`                | Denota un carácter de retroceso (BS)                   |
| `\<octal>`          | Denota un código de caracteres en el rango de 0 a 255. |

El `<octal>` anterior consta de uno, dos o tres dígitos octales ('0' a '7') que representan un número entre 0 y 255 (decimal).

Tenga en cuenta que una barra invertida seguida de cualquier otro carácter es una secuencia de escape no válida.
Las secuencias de escape no válidas son tratadas como errores de compilación por el JLS.

### Escapes Unicode
Además de las secuencias de escape de cadenas y caracteres descritas anteriormente,
Java tiene un mecanismo de escape Unicode más general, como se define en JLS 3.3. Escapes Unicode.
Un escape Unicode tiene la siguiente sintaxis:
```java
'\' 'u' <hex-digit> <hex-digit> <hex-digit> <hex-digit>
```
Donde <hex-digit> es uno de `'0'`, `'1'`, `'2'`, `'3'`, `'4'`, `'5'`, `'6'`, `'7'`, `'8'`, `'9'`, `'a'`, `'b'`, `'c'`, `'d'`,
`'e'`,`'f'`,`'A'`, `'B'`, `'C'`, `'D'`, `'E'`, `'F'`.

El compilador de Java asigna un escape Unicode a un carácter (estrictamente una unidad de código Unicode de 16 bits),
y se puede utilizar en cualquier lugar del código fuente donde el carácter asignado sea válido.
Se utiliza comúnmente en los literales de caracteres y cadenas cuando se necesita representar un carácter que no sea ASCII en un literal.
