# Constructor Con Argumentos
Los constructores se pueden crear con cualquier tipo de argumentos.
```java
public class TestClass {
    
    private String testData;
    
    public TestClass(String testData) {
        this.testData = testData;
    }
}
```
Llamado así:
```java
TestClass testClass = new TestClass("Test Data");
```
Una clase puede tener varios constructores con diferentes firmas.
Para encadenar llamadas de constructor (llame a un diferente Constructor de la misma clase al instanciar) 
use `this()`.
```java
public class TestClass {
    private String testData;
    public TestClass(String testData) {
        this.testData = testData;
    }
    public TestClass() {
        this("Test"); // testData defaults to "Test"
    } 
}
```
Llamado asi:
```java
TestClass testClass1 = new TestClass("Test Data");
TestClass testClass2 = new TestClass();
```