# Constructor Por Default

El "default" para los constructores es que no tienen ningún argumento.
En caso de que no especifique ningún constructor, el compilador generará un constructor predeterminado para usted.

Esto significa que los siguientes dos fragmentos son semánticamente equivalentes:
```java
public class TestClass{
    private String test;
}
public class TestClass {
    private String test; 
    public TestClass() {
        
    }
}
```
La visibilidad del constructor predeterminado es la misma que la visibilidad de la clase.
Por lo tanto, un paquete definido por clase tiene un constructor predeterminado de paquete privado

Sin embargo, si tiene un constructor no predeterminado,
el compilador **no generará** un constructor predeterminado para usted.
Así que estos no son equivalentes:
```java
public class TestClass{
    private String test;
    public TestClass(String arg){
        
    }
}

public class TestClass { 
    private String test;
    public TestClass() { }
    public TestClass(String arg) {
        
    } 
}
```
Tenga en cuenta que el constructor generado no realiza ninguna inicialización no estándar. 
Esto significa que todos los campos de su clase tendrán su valor predeterminado, a menos que tengan un inicializador.
```java
public class TestClass {
    private String testData;
    public TestClass() { 
        testData = "Test";
    } 
}
```
El contructor se llaman asi:
```java
TestClass testClass = new TestClass();
```