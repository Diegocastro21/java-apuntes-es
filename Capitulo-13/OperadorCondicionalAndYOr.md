# Operador Condicional-And y Condicional-or (&& y ||)

Java proporciona un operador condicional-and condicional-or, que toman uno o dos operandos de tipo `boolean` y producen un resultado `boolean`. Estos son:

* && - el operador condicional Y,
* || - los operadores condicional-OR. La evaluación de <left-expr> && <right-expr> es equivalente a la Siguiente pseudocódigo:

```java
{
    boolean L= evaluate(<left-expr>);
    if(L){
        return evaluate(<right-expr>);
    }else{
        // short-circuit the evaluation of the 2nd operand expression
        return false;
    }
}
```
La evaluación de `<left-expr> || <right-expr>` es equivalente al siguiente pseudocódigo:
```java
{
    boolean L = evaluate(<left-expr>);
    if (!L) {
        return evaluate(<right-expr>); 
    } else {
       // short-circuit the evaluation of the 2nd operand expression
        return true; 
    }
}
```
Como ilustra el pseudocódigo anterior, el comportamiento de los operadores de cortocircuito es equivalente al uso de instrucciones if / else.

### Ejemplo: usar && como guardia en una expresión

El siguiente ejemplo muestra el patrón de uso más común para el operador `&&`. 
Compare estas dos versiones de un método para probar si un `Integer` suministrado es cero.
```java
public boolean isZero(Integer value) {
    return value == 0;
}
public boolean isZero(Integer value) { 
    return value != null && value == 0;
}
```
La primera versión funciona en la mayoría de los casos, pero si el argumento del valor es `null`, se lanzará una `NullPointerException`.

En la segunda versión hemos añadido una prueba de "guardia". `value != null && ==  0` ¡La expresión se evalúa primero realizando la prueba `value != null`. 
Si la prueba `null` tiene éxito (es decir, se evalúa como `true`), entonces se evalúa la expresión del `value == 0`.
Si la prueba null falla, entonces la evaluación del `valor == 0` se omite (circuito cortocircuitado), y no obtenemos una `NullPointerException`.

### Ejemplo: usar && para evitar un cálculo costoso

El siguiente ejemplo muestra cómo se puede usar `&&` para evitar un cálculo relativamente costoso:
```java
public boolean verify(int value, boolean needPrime) {
    return !needPrime | isPrime(value);
}
public boolean verify(int value, boolean needPrime) { 
    return !needPrime || isPrime(value);
}
```
En la primera versión, ambos operandos del `|` siempre se evaluarán, por lo que el método isPrime (caro) se llamará innecesariamente.
La segunda versión evita la llamada innecesaria usando `||` en lugar de `|`.