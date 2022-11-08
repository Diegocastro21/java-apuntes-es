# El operador Lambda ( -> )

A partir de Java 8, el operador Lambda ( -> ) es el operador utilizado para introducir una expresión Lambda.
Hay dos sintaxis comunes, como lo ilustran estos ejemplos:
> Version ≥ Java SE 8
```java
 a -> a + 1             // Una lambda que añade uno a su argumento
a -> { return a + 1; }  // Una lambda equivalente usando un bloque.
```
Una expresión lambda define una función anónima, o más correctamente una instancia de una clase anónima que implementa una interfaz funcional.

(Este ejemplo se incluye aquí para su integridad. Consulte el tema de expresiones de lambda para obtener el tratamiento completo.)