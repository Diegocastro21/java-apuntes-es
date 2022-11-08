# El Primitivo double
Un `double` es un número de coma flotante IEEE 754 de 64 bits de doble precisión.
```java
double example = -7162.37;
double myDouble = 974.21;
double anotherDouble = 658.7;

double addedDoubles = myDouble + anotherDouble;         // 315.51 
double subtractedDoubles = myDouble - anotherDouble;    // 1632.91
        
double scientificNotationDouble = 1.2e-3;               // 0.0012
```
Debido a la forma en que se almacenan los números de coma flotante, muchos números no tienen una representación exacta.
```java
 double notExact = 1.32 - 0.42;     // resultado deberia ser 0.9
System.out.println(notExact);       // 0.9000000000000001
```
Si bien el uso de `double` está bien para la mayoría de las aplicaciones,
ni `float` ni `double` deben usarse para almacenar números precisos como la moneda.
En su lugar, se debe usar la clase `BigDecimal`

El valor predeterminado de un `double` es 0,0d
```java
public double defaultDouble; // defaultDouble == 0.0
```
Nota: `Double.POSITIVE_INFINITY`, `Double.NEGATIVE_INFINITY`, `Double.NaN` son valores `double`.
`NaN` significa resultados de operaciones que no se pueden determinar, como dividir 2 valores infinitos.
Además, `0d` y `-0d` son diferentes, pero == es cierto:
```java
double d1 = 0d;
double d2 = -0d;
System.out.println(d1 == d2); // true
System.out.println(1d / d1); // Infinity
System.out.println(1d / d2); // -Infinity 
System.out.println(Double.POSITIVE_INFINITY / Double.POSITIVE_INFINITY); // NaN
```