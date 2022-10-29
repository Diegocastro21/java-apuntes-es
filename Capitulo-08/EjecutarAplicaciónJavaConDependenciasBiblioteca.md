# Ejecutar Una Aplicación Java Con Dependencias De Biblioteca

Esta es una continuación de los ejemplos de "clase principal" y "JAR ejecutable".

Las aplicaciones típicas de Java consisten en un código específico de la aplicación y varios códigos de biblioteca reutilizables
que usted ha implementado o que ha sido implementado por terceros. Estas últimas se conocen comúnmente como dependencias de bibliotecas
y normalmente se empaquetan como archivos JAR.

Java es un lenguaje vinculado dinámicamente. Cuando se ejecuta una aplicación Java con dependencias de biblioteca, la JVM 
necesita saber dónde están las dependencias para poder cargar las clases según sea necesario. En términos generales, 
hay dos formas de lidiar con esto:

* La aplicación y sus dependencias se pueden reempaquetar en un solo archivo JAR que contiene todas las clases y recursos necesarios.
* Se puede decir a la JVM dónde encontrar los archivos JAR dependientes a través de la ruta de clase en tiempo de ejecución.

Para un archivo JAR ejecutable, la ruta de clase en tiempo de ejecución se especifica mediante el atributo de manifiesto "Class-Path". 
_(Nota editorial: Esto debe describirse en un tema separado en el comando jar)_. De lo contrario, el camino de clase en tiempo de ejecución debe 
suministrarse utilizando la opción -cp o utilizando la variable de entorno CLASSPATH.

Por ejemplo, supongamos que tenemos una aplicación Java en el archivo "myApp.jar" cuya clase de punto de entrada es `com.example.MyApp`.
Supongamos también que la aplicación depende de los archivos JAR de la biblioteca "lib/library1.jar" y "lib/library2.jar". 
Podríamos iniciar la aplicación usando el comando java de la siguiente manera en una línea de comandos:
```clickhouse
$ Alternative 1 (preferred)
$ java -cp MyApp.jar:lib/library1.jar:lib/library2.jar com.example.MyApp
$ # Alternative 2
$ export CLASSPATH=myApp.jar:lib/library1.jar:lib/library2.jar
$ java com.example.MyApp

```

(En Windows, usarías ; en lugar de : como separador de ruta de clase, y establecerías la variable CLASSPATH (local) usando set en lugar de exportar).

Si bien un desarrollador de Java se sentiría cómodo con eso, no es "friendly para el usuario". Por lo tanto, es una práctica común escribir un simple script de shell (o un archivo por lotes de Windows) 
para ocultar los detalles que el usuario no necesita saber. Por ejemplo, si pones el siguiente script de shell en un archivo llamado "myApp", lo hiciste ejecutable y lo pones en un directorio en la ruta de búsqueda de comandos:

```clickhouse
#!/bin/bash
# The 'myApp' wrapper script
export DIR=/usr/libexec/myApp
export CLASSPATH=$DIR/myApp.jar:$DIR/lib/library1.jar:$DIR/lib/library2.jar 
java com.example.MyApp
```
Entonces podrías ejecutarlo de la siguiente manera:
```clickhouse
$ myApp arg1 arg2 ...
```
Cualquier argumento en la línea de comandos se pasará a la aplicación Java a través de la expansión "$@". 
(Puedes hacer algo similar con un archivo por lotes de Windows, aunque la sintaxis es diferente).

