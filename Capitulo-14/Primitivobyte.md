# El Primitivo Byte

Un `byte` es un entero con signo de 8 bits.
Puede almacenar un valor mínimo de -27 (-128) y un valor máximo de 27 - 1 (127)
```java
byte example = -36;
byte myByte = 96;
byte anotherByte = 7;

byte addedBytes = (byte) (myByte + anotherByte);        // 103
byte subtractedBytes = (byte) (myBytes - anotherByte);  // 89
```
Los valores máximos y mínimos de los `byte` se pueden encontrar en:
```java
byte high = Byte.MAX_VALUE; // high == 127
byte low = Byte.MIN_VALUE; // low == -128
```
El valor predeterminado de `byte` es 0
```java
byte defaultByte;   // defaultByte == 0
```