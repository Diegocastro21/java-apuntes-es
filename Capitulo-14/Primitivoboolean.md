# El Primitivo Boolean
Un booleano puede almacenar uno de dos valores, ya sea verdadero o falso
```java
boolean foo = true;
System.out.println("foo = " + foo);             // foo = true

boolean bar = false; 
System.out.println("bar = " + bar);             // bar = false

boolean notFoo = !foo;
System.out.println("notFoo = " + notFoo);       // notFoo = false

boolean fooAndBar = foo && bar;
System.out.println("fooAndBar = " + fooAndBar); //fooAndBar = false

boolean fooOrBar = foo || bar;
System.out.println("fooOrBar = " + fooOrBar);   // fooOrBar = true

boolean fooXorBar = foo ^ bar;
System.out.println("fooXorBar = " + fooXorBar); // fooXorBar = true
```
EL valor predeterminado de `boolean` es false:
```java
boolean defaultBoolean;  //defaultBoolean == false
```