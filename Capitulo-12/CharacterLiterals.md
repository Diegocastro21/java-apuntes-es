# Character literals

Los literales de caracteres proporcionan la forma más conveniente de expresar valores de `char` en el código fuente de Java.
Un carácter literal consta de:

* Un carácter de apertura de una sola comillas (').
* Una representación de un Caracter. Esta representación no puede ser un carácter de comillas únicas o de salto de línea, pero puede ser una secuencia de escape introducida por un carácter de barra invertida (\); consulte Secuencias de escape en literales.
* Un carácter de cierre de una sola comilla (').

Por Ejemplo:
```java
char a = 'a';
char doubleQuote = '"';
char singleQuote = '\'';
```
Un salto de línea en un carácter literal es un error de compilación:
```java
char newline = '
// Error De Compilacion En la linea anterior
char newLine = '\n'; // Correct
```