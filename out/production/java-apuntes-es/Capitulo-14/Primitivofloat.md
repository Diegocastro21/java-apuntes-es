# El Primitivo float
Un `float` es un número de coma flotante IEEE 754 de 32 bits de precisión única. Por defecto,
los decimales se interpretan como dobles. Para crear un `float`, simplemente añade una `f` al literal decimal.
```java
double doubleExample = 0.5; float floatExample = 0.5f;      // Sin 'f' después de los dígitos = double
float myFloat = 92.7f;                                      // con 'f' despues de los digitos = float 

float positiveFloat = 89.3f;                                // esto es un float...
float negativeFloat = -89.3f;                               // Puede ser positivo
float integerFloat = 43.0f;                                 // o negativo
float underZeroFloat = 0.0549f;                             // puede ser un valor fraccionario inferior que 0
```
Los floats manejan las cinco operaciones aritméticas comunes: suma, resta, multiplicación, división y módulo.

Nota: Lo siguiente puede variar ligeramente como resultado de errores de coma flotante. 
Algunos resultados se han redondeado con fines de claridad y legibilidad
(es decir, el resultado impreso del ejemplo de adición fue en realidad 34.600002).
```java
// suma
float result = 37.2f + -2.6f;   // resultado: 34.6
        
// resta
float result = 45.1f - 10.3f;    // resultado: 34.8

// multiplicacion
float result = 26.3f * 1.7f;    // resultado: 44.71

// division
float result = 37.1f / 4.8f;    // resultado: 7.729166

// modulus
float result = 37.1f % 4.8f;    // resultado: 3.4999971
```
Debido a la forma en que se almacenan los números de coma flotante (es decir, en forma binaria), 
muchos números no tienen una representación exacta.
```java
 float notExact = 3.1415926f;
System.out.println(notExact); // 3.1415925
```
Si bien el uso de `float` está bien para la mayoría de las aplicaciones,
no se deben usar `float` ni `double` para almacenar representaciones exactas de números decimales (como cantidades monetarias)
o números donde se requiere una mayor precisión.
En su lugar, se debe usar la clase `BigDecimal`.

El valor predeterminado de un `float` es 0.0f.
```java
float defaultFloat;  // defaultFloat == 0.0f 
```
Un `float` es preciso para aproximadamente un error de 1 entre 10 millones.

Nota: `Float.POSITIVE_INFINITY`, `Float.NEGATIVE_INFINITY`, `Float.NaN` son valores `float`.
NaN significa resultados de operaciones que no se pueden determinar, 
como dividir 2 valores infinitos. Además, `0f` y `-0f` son diferentes, 
pero == rinde cierto:
```java
float f1 = 0f;
float f2 = -0f;
System.out.println(f1 == f2); // true
System.out.println(1f / f1); // Infinity
System.out.println(1f / f2); // -Infinity
System.out.println(Float.POSITIVE_INFINITY / Float.POSITIVE_INFINITY); // NaN
```