# EL Literal Null
El literal nulo (escrito como nulo) representa el único valor del tipo nulo.
Aquí hay algunos ejemplos
```java
MyClass object = null;
MyClass[] objects = new MyClass[]{new MyClass(), null, new MyClass()};

myMethod(null);

if (objects != null) { 
    // Do something
}
```
El tipo null es bastante inusual. No tiene nombre, por lo que no puedes expresarlo en el código fuente de Java. 
(Y tampoco tiene representación en tiempo de ejecución).

El único propósito del tipo null es ser el tipo `null`.
Es compatible con todos los tipos de referencia y se puede convertir en cualquier tipo de referencia.
(En este último caso, el reparto no implica una comprobación de tipo de tiempo de ejecución).

Finalmente, `null` tiene la propiedad que `null instanceof <SomeReferenceType>` evaluará como false,
sin importar cuál sea el tipo.