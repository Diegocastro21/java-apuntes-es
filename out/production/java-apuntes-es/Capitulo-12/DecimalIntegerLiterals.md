# Decimal Integer Literals
Los literales enteros proporcionan valores que se pueden usar cuando se necesita una instancia de
byte, short, int, long o char. 
(Este ejemplo se centra en las formas decimales simples.
Otros ejemplos explican cómo hacer literales en octal, hexadecimal y binario, y el uso de guiones bajos para mejorar la legibilidad.)

### Literales enteros ordinarios
```java
0  // EL numero decimal zero (type 'int')
1  // EL numero decimal uno (type 'int')
42 // EL numero decimal cuarenta y dos (type 'int')
```
Tienes que tener cuidado con los ceros principales.
Un cero inicial hace que un literal entero se interprete como octal y no decimal.
```java
077 // Este literal actualmente significa 7 x 8 + 7 ... or 63 decimal!
```

Los literales enteros no están firmados. Si ves algo como `-10` o `+10`,
en realidad estas son expresiones que usan el unario - Y operadores unarios +.

El rango de literales enteros de esta forma tiene un tipo intrínseco de `int`, y debe caer en el rango de cero a 231 o
2.147.483.648.

Tenga en cuenta que 231 es 1 mayor que `Integer.MAX_VALUE`. Los literales de 0 a `2147483647` se pueden usar en cualquier lugar,
pero es un error de compilación usar 2147483648 sin un operador unario `-` anterior. 
(En otras palabras, está reservado para expresar el valor de `Integer.MIN_VALUE`.)
```java
int max = 2147483647; // OK
int min = -2147483648; // OK
int tooBig = 2147483648; // ERROR
```

### Literals enteros largos
Los literales de tipo `long` se expresan añadiendo un sufijo `L`. Por ejemplo:
```java
0L // The decimal number zero (type 'long') 
1L // The decimal number one (type 'long') 
2147483648L // The value of Integer.MAX_VALUE + 1
        
long big = 2147483648;   // ERROR 
long big2 = 2147483648L; // OK
```
Tenga en cuenta que la distinción entre `int` y literales `long` es significativa en otros lugares.
Por ejemplo:
```java
int i = 2147483647;
long l = i + 1;            // Produce un valor negativo porque la operación es
                           // Realizado usando aritmética de 32 bits, y el
                           // Excesos adicionales
long l2 = i + 1L;          // Produce el valor (intuitivamente) correcto.
```
