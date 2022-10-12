# Casting de primitivos No Numericos

El tipo de dato `boolean` no puede convertir ni ser convertido con ningún otro tipo de dato primitivo

Un `char` puede convertir o ser convertido con cualquier tipo numérico utilizando los mapeos de puntos de código
especificados por **Unicode**.
Un `char` se representa en la memoria como un valor entero de 16 bits sin signo (2 bytes),
por lo que la conversión a `byte`(1 byte) eliminará 8 de esos bits (esto es seguro para los caracteres ASCII).

Los métodos de utilidad de la clase `Character` usa `int`(4 bytes) para transferir a/desde valores de punto de código,
pero un `short` (2 bytes) también sería suficiente para almacenar un Unicode code-point.

`int malInt = (int) true;` Error de Compilacion --> Tipos Incompatibles

`char char01 = (char) 69;` E

`byte byte01 = (byte) 'E'` 69

`short short01 = (short) 'E'` 69

`int int1 = (int) 'E'` 69

```java
char char2 = (char) 8253;
byte byte2 = (byte) '‽';
short short2 = (short) '&';
int int2 = (int) '&';
```
salida:
```java
‽
61
38
38
```