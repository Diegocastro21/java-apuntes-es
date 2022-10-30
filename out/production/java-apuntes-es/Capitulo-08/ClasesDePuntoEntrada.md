# Clases De Punto De Entrada

Una clase de punto de entrada Java tiene un método principal con las siguientes firmas y modificadores:
```java
public static void main(String[] args)
```

> Nota al margen: debido a cómo funcionan las matrices, también puede ser (`String args[]`)

Cuando el comando java inicia la máquina virtual, carga las clases de punto de entrada especificadas e intenta encontrar
la `main`. Si tiene éxito, los argumentos de la línea de comandos se convierten en objetos Java **String** y se ensamblan en una matriz. 
Si `main` se invoca así, la matriz no será **null** y no contendrá ninguna entrada **nula**.

Un método de clase de **punto de entrada** válido debe hacer lo siguiente:

* Ser nombrado `main` (sensible a mayúsculas y minúsculas)
* Ser `public` y `static`.
* Tener un tipo de devolución `void`.
* Tener un solo argumento con una cadena de `String[]`. El argumento debe estar presente y no se permite más de un argumento.
* Sé genérico: los parámetros de tipo no están permitidos.
* Tener una clase de nivel superior no genérica (no anidada ni interna).

Es convencional declarar la clase como `public`, pero esto no es estrictamente necesario.
A partir de Java 5, el tipo de argumento del método `main` puede ser un varargs de **String** en lugar de una string array.
`main` puede lanzar excepciones opcionalmente, y su parámetro puede ser nombrado cualquier cosa, pero convencionalmente es `args`.

### Puntos de entrada de JavaFX

A partir de Java 8, el comando java también puede iniciar directamente una aplicación JavaFX.
JavaFX está documentado en la etiqueta JavaFX, pero un punto de entrada de JavaFX debe hacer lo siguiente:

* Extend `javafx.application.Application`.
* Ser **public** y no **abstract**.
* No ser genérico ni anidado.
* Tener un constructor **public** no-args explícito o implícito.