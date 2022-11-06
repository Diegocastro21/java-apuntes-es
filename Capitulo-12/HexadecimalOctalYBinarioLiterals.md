# Hexadecimal, Octal Y Binary literals
Un número hexadecimal es un valor en la base-16. Hay 16 dígitos, `0-9` y las letras A-F (el caso no importa).
A-F representa `10-16`.

Un número octal es un valor en base-8 y utiliza los dígitos `0-7`.

Un número binario es un valor en base-2, y utiliza los dígitos 0 y 1.

Todos estos números dan como resultado el mismo valor, `110`:
```java
int dec = 110; //  Sin Prefijo   --> decimal literal
int bin = 0b1101110; //  Prefijo '0b'  --> binary literal
int oct = 0156; // Prefijo '0'   --> octal literal
int hex = 0x6E; // Prefijo '0x'  --> hexadecimal literal
```

Tenga en cuenta que la sintaxis literal binaria se introdujo en Java 7.

El literal octal puede ser fácilmente una trampa para los errores semánticos.
Si defines un '0' a la izquierda a tus literales decimales, obtendrás el valor equivocado:
```java
int a = 0100;  // Instancia de 100, a == 64
```