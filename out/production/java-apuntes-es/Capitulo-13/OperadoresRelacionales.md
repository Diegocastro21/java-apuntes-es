# Los Operadores Relacionales (<, <=, >, >=)
Los operadores `<`, `<=`, `>` y `>=` son operadores binarios para comparar tipos numéricos.
El significado de los operadores es como Lo esperarías.
Por ejemplo, si a y b se declaran como cualquiera de los tipos `byte`, `short`, `char`, `int`, `long`, `float`, `double` o
los tipos en caja correspondientes:
```java
- `a < b` comprueba si el valor de `a` es menor que el valor de `b`.

- `a <= b` comprueba si el valor de `a` es menor o igual al valor de `b`.

- `a > b` comprueba si el valor de `a` es mayor que el valor de `b`.

- `a >= b` comprueba si el valor de `a` es mayor o igual al valor de `b`.
```
El tipo de resultado para estos operadores es booleano en todos los casos.

Los operadores relacionales se pueden utilizar para comparar números con diferentes tipos. Por ejemplo:
```java
int i = 1;
long l = 2;
if (i < l) {
    System.out.println("i is smaller");
}
```
Los operadores relacionales se pueden utilizar cuando uno o ambos números son instancias de tipos numéricos en caja. Por ejemplo:
```java
Integer i = 1;  // 1 is autoboxed to an Integer
Integer j = 2;  // 2 is autoboxed to an Integer 
if (i < j) {
    System.out.println("i is smaller");
}
```

El comportamiento preciso se resume de la siguiente manera:

1. Si uno de los operandos es un tipo en caja, se desempaqueta.

2. Si cualquiera de los operandos ahora es un `byte`, `short` o `char`, se promueve a un `int`.

3. Si los tipos de los operandos no son los mismos, entonces el operando con el tipo "más pequeño" se promueve al
Tipo "más grande".

4. La comparación se realiza en los valores `int`, `long`, `float` o `double` resultantes.

Debes tener cuidado con las comparaciones relacionales que implican números de coma flotante:

* Las expresiones que calculan números de coma flotante a menudo incurren en errores de redondeo debido al hecho de que las representaciones de coma flotante del ordenador tienen una precisión limitada.
* Al comparar un tipo entero y un tipo de coma flotante, la conversión del entero a coma flotante también puede provocar errores de redondeo.

Por último, Java admite el uso de operadores relacionales con cualquier tipo que no sea los enumerados anteriormente.
Por ejemplo, no puedes usar estos operadores para comparar cadenas, matrices de números, etc.

