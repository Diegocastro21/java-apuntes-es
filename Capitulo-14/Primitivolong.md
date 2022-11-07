# El Primitivo Long
Por defecto, `long` es un entero con signo de 64 bits (en Java 8, puede ser con o sin signo).
Firmado, puede almacenar un valor mínimo de -263 y un valor máximo de 263 - 1,
y sin firmar puede almacenar un valor mínimo de 0 y un valor máximo de 264 - 1
```java
long example = -42;
long myLong = 284;
long anotherLong = 73;

//Una "L" debe añadirse al final del número, porque por defecto,
//Se supone que los números son del tipo int. La aplicación de una "L" lo convierte en una long
//Como 549755813888 (2 ^ 39) es mayor que el valor máximo de un int (2^31 - 1),, 
// "L" debe adjuntarse
        
long bigNumber = 549755813888L;

long addedLongs = myLong + anotherLong;         // 284 + 73 = 357
long subtractedLongs = myLong - anotherLong;    // 284 - 73 = 211
```
Los valores máximos y mínimos de `long` se pueden encontrar en:
```java
long high = Long.MAX_VALUE;     // high == 9223372036854775807L
long low = Long.MIN_VALUE;      // low == -9223372036854775808L
```
EL valor predeterminado de un `long` es 0L
```java
long defaultLong; // defaultLong == 0L
```
Nota: la letra "L" anexa al final del literal `long` no distingue entre mayúsculas y minúsculas,
sin embargo, es una buena práctica usar mayúsculas, ya que es más fácil de distinción del dígito uno:
```java
2L == 2l;  // true
```

Advertencia: Java almacena en caché las instancias de objetos enteros del rango -128 a 127.

Se pueden encontrar los siguientes resultados:
```java
Long val1 = 127L;
Long val2 = 127L;

System.out.println(val1 == val2);   // true
        
Long val3 = 128L;
Long val4 = 128L;
System.out.println(val3 == val4);   // false
```
Para comparar correctamente 2 valores de Object Long, utilice el siguiente código (desde Java 1.7 en adelante):
```java
Long val3 = 128L;
Long val4 = 128L;

System.out.println(Objects.equal(val3, val4)); // true
```
Comparar un primitivo `long` con un objeto `long` no dará lugar a un falso negativo como comparar 2 objetos con == hace.