# Ejecutar Una Aplicación Java A Través De Una Clase "main"

Cuando una aplicación no se ha empaquetado como un JAR ejecutable, debe proporcionar el nombre de una clase de punto de entrada en la línea de comandos java.

Ejecutar la clase de HelloWorld

El ejemplo **"HelloWorld"** se describe en Creación de un nuevo programa Java. Consiste en una sola clase llamada HelloWorld que cumple con los requisitos para un punto de entrada.

Suponiendo que el archivo **"HelloWorld.class"** (compilado) esté en el directorio actual, se puede iniciar de la siguiente manera:
```java
java HelloWorld
```

Algunas cosas importantes a tener en cuenta son:

* Debemos proporcionar el nombre de la clase: no el nombre de la ruta del archivo ".class" o el archivo ".java".
* Si la clase se declara en un paquete (como la mayoría de las clases de Java), entonces el nombre de clase que
suministramos al comando java debe ser el nombre completo de la clase. Por ejemplo, si SomeClass se declara en el paquete com.example,
el nombre completo de la clase será com.example.SomeClass.

Especificar una ruta de clase

A menos que estemos usando en la sintaxis de comando java -jar, el comando java busca que la clase se cargue buscando en
la ruta de clase; consulte La ruta de clase. El comando anterior depende de que la ruta de clase predeterminada sea (o incluya) 
el directorio actual. Podemos ser más explícitos sobre esto especificando la ruta de clase que se utilizará usando la opción `-cp`.
```java
java -cp . HelloWorld
```
Esto dice que el directorio actual (que es a lo que se refiere ".") sea la única entrada en la ruta de clase.

El -cp es una opción que procesa el comando java. Todas las opciones destinadas al comando java deben estar antes del nombre de la clase.
Cualquier cosa después de la clase se tratará como un argumento de línea de comandos para la aplicación Java, y se pasará a la aplicación en la **string[]** que se pasa al método `main`.

(Si no se proporciona ninguna opción -cp, el java utilizará la ruta de clase dada por la variable de entorno CLASSPATH. Si esa variable no está configurada o vacía, java utiliza "." como ruta de clase predeterminada.)