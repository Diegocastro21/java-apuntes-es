# Llamar Al Constructor Padre
Digamos que tienes una clase de padres y una clase de niños.
Para construir una instancia secundaria siempre requiere que se ejecute algún
constructor principal en el mismo gebinning del constructor hijo.
Podemos seleccionar el constructor principal que queramos llamando explícitamente a `super(...)` 
con los argumentos apropiados como nuestra primera declaración de constructor hijo.
Hacer esto nos ahorra tiempo reutilizando el constructor de las clases padres en lugar
de reescribir el mismo código en el constructor de las clases secundarias.

### Sin el método `super(...)`:
(Inplicitamente, la versión no-args `super()` se llama invisiblemente)
```java
class Parent {
    private String name;
    private int age;
    public Parent() {} // Necesario porque llamamos a super() sin argumentos
    public Parent(String tName, int tAge) { 
        name = tName;
        age = tAge; 
    }
}
// Esto ni siquiera se compila, porque el nombre y la edad son privados, 
// haciéndolos invisibles incluso para la clase infantil.
class Child extends Parent {
    public Child() {
        // El compilador llama implícitamente a super() aquí
        name = "Jhon";
        age = 42;
    } 
}
```

### Con el metodo `super()`:
```java
class Parent {
    private String name;
    private int age;
    public Parent(String tName, int tAge) {
        name = tName;
        age = tAge; 
    }
}
class Child extends Parent { 
    public Child() {
        super("John", 42);  // explicit super-call
    }
}
```
Nota: Las llamadas a otro constructor (encadenamiento) o al superconstructor **DEBEN** ser
la primera declaración dentro del constructor.

Si llamas explícitamente al constructor `super(...)`, 
debe existir un constructor padre coincidente (eso es sencillo, ¿verdad?).

Si no llama explícitamente a ningún constructor `super(...)`, 
su clase principal debe tener un constructor no-args, 
y esto se puede escribir explícitamente o crear de forma predeterminada
por el compilador si la clase padre no proporciona ningún constructor.

```java
class Parent{
    public Parent(String tName, int tAge) {}
}
class Child extends Parent{ 
    public Child(){}
}
```
La clase Padre no tiene un constructor predeterminado,
por lo que el compilador no puede añadir `super` en el constructor hijo.
Este código no se compilará. Debes cambiar los constructores para que se ajusten a ambos lados,
o escribir tu propia `súper` llamada, así:
```java
class Child extends Parent{ 
    public Child(){
        super("juanito", 50);
    }
}
```