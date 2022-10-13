# Casting De Objetos

Al igual que con los tipos primitivos, los objetos pueden ser casteados tanto explícita como implícitamente.

El casting implícito se produce cuando el tipo de origen extiende o implementa el tipo de destino
(casting a una superclase o interfaz).

El casting explícito tiene que hacerse cuando el tipo de origen es extendido o implementado por el tipo de destino
(casting a un subtipo). Esto puede producir una excepción en tiempo de ejecución (`ClassCastException`) cuando el objeto que se está casteando no es del tipo de destino (o del subtipo de destino)


```java
Float variable_float = new Float(32.0f);

Number n = variable_float;  //Implicita (Debido a que Float Extiende de Number)
public final class Float extends Number
        implements Comparable<Float>, Constable, ConstantDesc {}
        
Float variable_float2 = (Float) n; Explicita
Double variable_double = (Double) n; 
// Lanza una excepcion ClassCastException (Debido a que la clase Float no puede ser casteado por la clase Double)
```
**`java.lang.ClassCastException: class java.lang.Float cannot be cast to class java.lang.Double`**
