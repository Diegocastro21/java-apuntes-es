# Instanciación De Un Tipo De Referencia

```java
Object obj = new Object();  // Nota la palabra 'new'
```
Dónde:

* El `Object` es un tipo de referencia.
* obj es la variable en la que se almacena la nueva referencia.
* `Object()` es la llamada a un constructor de `Object`.

Qué pasa:

* El espacio en la memoria está asignado para el objeto.
* El constructor `Object()` se llama para inicializar ese espacio de memoria.
* La dirección de memoria se almacena en obj, de modo que hace referencia al objeto recién creado.

Esto es diferente de los primitivos:
```java
int i = 10;
```
Donde el valor actual 10 es guardado en `i`.