# El Primitivo int
Un tipo de datos primitivo como `int` contiene valores directamente en la variable que lo está usando,
mientras que una variable que se declaró usando `Integer` contiene una referencia al valor.

Según la API de java: 
"La clase Integer envuelve un valor del tipo primitivo int en un objeto. Un objeto de tipo Entero contiene un solo campo cuyo tipo es int".

Por defecto, `int` es un entero con signo de 32 bits. Puede almacenar un valor mínimo de -231 y un valor máximo de 231 - 1.
```java
int example = -42;
int myInt = 284;
int anotherInt = 73;

int addedInts = myInt + anotherInt;         // 284 + 73 = 357
int subtractedInts = myInt - anotherInt;    // 284 - 73 = 211
```

Si necesita almacenar un número fuera de este rango, se debe usar `long` en su lugar. 
Exceder el rango de valores de `int` conduce a un desbordamiento de enteros,
haciendo que el valor que exceda el rango se agregue al sitio opuesto del rango
(El positivo se vuelve negativo y viceversa). El valor es
`((value - MIN_VALUE) % RANGE) + MIN_VALUE, or ((value + 2147483648) % 4294967296) - 2147483648`
```java
int demo = 2147483647; //maximo entero positivo
System.out.println(demo); //prints 2147483647 
demo = demo + 1; //leads to an integer overflow 
System.out.println(demo); // prints -2147483648
```
Los valores máximos y mínimos de `int` se pueden encontrar en:
```java
int high = Integer.MAX_VALUE;   // high == 2147483647 
int low = Integer.MIN_VALUE;    // low == -2147483648
```
El valor predeterminado el un `int` es 0
```java
int defaultInt = 0; // defaultInt == 0
```