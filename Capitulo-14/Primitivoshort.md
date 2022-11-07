# El Primitivo short

Un `short` es un entero con signo de 16 bits.
Tiene un valor mínimo de -215 (-32 768), y un valor máximo de 215 -1 (32.767)
```java
short example = -48;
short myShort = 987;
short anotherShort = 17;

short addedShorts = (short) (myShort + anotherShort);       // 1,004 
short subtractedShorts = (short) (myShort - anotherShort);  // 970
```
Los valores máximos y mínimos de `short` se pueden encontrar en:
```java
short high = Short.MAX_VALUE; // high == 32767 
short low = Short.MIN_VALUE; // low == -32768
```
El valor predeterminado de `short` es 0;
```java
short defaultShort; // defaultShort == 0
```