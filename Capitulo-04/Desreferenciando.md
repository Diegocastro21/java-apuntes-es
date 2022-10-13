# Desreferenciado

La desreferenciación se realiza con el operador **.**

```java
Object obj = new Object();
String texto = obj.toString(); // 'obj' is desreferenciado
```

La desreferencia sigue la dirección de memoria almacenada en una referencia,
hasta el lugar de la memoria donde reside el objeto real. Cuando se encuentra un objeto, se llama al método solicitado (toString en este caso).

Cuando una referencia tiene el valor `null`, la desreferenciación da como resultado una `NullPointerException`:

```java
Object obj = null;
obj.toString(); // Lanza una excepcion del tipo NullPointerException
```

`Null` indica la ausencia de un valor, es decir, seguir la dirección de memoria no conduce a ninguna parte.
Por lo tanto, no hay ningún objeto en el que se pueda llamar al método solicitado.