# El Operador Instanceof 
Este operador comprueba si el objeto es de un tipo de clase/interfaz particular. El operador instanceof se escribe como:
```java
( Variable de referencia de objeto ) instanceof (class/interface tipo)
```
Ejemplo:
```java
public class Test {
    public static void main(String args[]){
        String name = "Booyah";
        // Lo siguiente devolverá true ya que el nombre es el tipo de String 
        boolean result = name instanceof String; 
        System.out.println( result ); // true
    }
}
```
Este operador seguirá devolviendo true si el objeto que se está comparando es la asignación compatible con el tipo de la derecha.

Ejemplo:
```java
class Vehicle {}

public class Car extends Vehicle {
    public static void main(String args[]){
        Vehicle a = new Car();
        boolean result = a instanceof Car;
        System.out.println( result ); // true
    } 
}
```