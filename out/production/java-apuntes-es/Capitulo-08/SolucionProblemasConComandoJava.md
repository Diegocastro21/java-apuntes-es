# Solución De Problemas Con El Comando "java"

Este ejemplo cubre los errores comunes con el uso del comando "java".

**"No se ha encontrado el comando"**

Si recibes un mensaje de error como:
```java
java: command not found
```

Al intentar ejecutar el comando java, esto significa que no hay ningún comando java en la búsqueda de comandos de tu shell.
La causa podría ser:

* No tienes un Java JRE o JDK instalado en absoluto,
* No ha actualizado la variable de entorno PATH (correctamente) en su archivo de inicialización del shell, o
* No ha "probargado" el archivo de inicialización relevante en el shell actual.

Consulte "Instalación de Java" para conocer los pasos que debe seguir.

### "No se pudo encontrar ni cargar la clase principal"

Este mensaje de error es enviado por el comando java si no ha podido encontrar / cargar la clase de punto de entrada que ha especificado.
En términos generales, hay tres razones generales por las que esto puede suceder:

* Has especificado una clase de punto de entrada que no existe.
* La clase existe, pero la has especificado incorrectamente.
* La clase existe y la has especificado correctamente, pero Java no puede encontrarla porque la ruta de clase es incorrecta.

Aquí hay un procedimiento para diagnosticar y resolver el problema: 

1. Averigua el nombre completo de la clase de punto de entrada.

    * Si tienes el código fuente de una clase, entonces el nombre completo consiste en el nombre del paquete y el nombre simple de la clase. La instancia de la clase "Main" se declara en el paquete "com.example.myapp", luego su nombre completo es "com.example.myapp.Main".
    * Si tienes un archivo de clase compilado, puedes encontrar el nombre de la clase ejecutando javap en él.
    * Si el archivo de clase está en un directorio, puede inferir el nombre completo de la clase de los nombres de los directorios.
    * Si el archivo de clase está en un archivo JAR o ZIP, puede inferir el nombre completo de la clase de la ruta del archivo en el archivo JAR o ZIP.

2. Mira el mensaje de error del comando java. El mensaje debe terminar con el nombre completo de la clase que java está intentando usar.

   * Comprueba que coincida exactamente con el nombre completo de la clase de entrada.
   * No debe terminar con ".java" o ".class".
   * No debe contener barras o ningún otro carácter que no sea legal en un identificador de Java1.
   * La carcasa del nombre debe coincidir exactamente con el nombre completo de la clase.

3. Si está utilizando el nombre de clase correcto, asegúrese de que la clase esté realmente en el camino de clase:

   * Resuelver el nombre de ruta al que se asigna el nombre de la clase; consulte Asignar nombres de clase a nombres de ruta
   * Descifique cuál es la ruta de clase; vea este ejemplo: Diferentes formas de especificar la ruta de clase
   * Mira cada uno de los archivos JAR y ZIP en la ruta de clase para ver si contienen una clase con el nombre de ruta requerido.
   * Mira cada directorio para ver si el nombre de ruta se resuelve en un archivo dentro del directorio.

Si al revisar la ruta de clase a mano no se encontró el problema, puede agregar las opciones `-Xdiag` y `-XshowSettings`.
El primero enumera todas las clases que se cargan, y el segundo imprime la configuración que incluye la ruta de clase efectiva para la JVM.

Por último, hay algunas causas oscuras para este problema:

* Un archivo JAR ejecutable con un atributo de `Main-Class`que especifica una clase que no existe.
* Un archivo JAR ejecutable con un atributo Class-Path incorrecto.
* Si estropeas las opciones antes del nombre de la clase, el comando java puede intentar interpretar una de Como el nombre de la clase.
* Si alguien ha ignorado las reglas de estilo de Java y ha utilizado identificadores de paquetes o clases que difieren solo en mayúsculas y minúsculas, y se está ejecutando en una plataforma que trata las mayúsculas de las letras en los nombres de archivo como no significativas.
* Problemas con los homoglifos en los nombres de las clases en el código o en la línea de comandos.

### "Método principal no encontrado en la clase <nombre>"

Este problema ocurre cuando el comando java es capaz de encontrar y cargar la clase que usted nombró, pero luego no puede encontrar un método de punto de entrada.

Hay tres posibles explicaciones:

* Si está intentando ejecutar un archivo JAR ejecutable, entonces el manifiesto del JAR tiene un atributo "Clase principal" incorrecto que especifica una clase que no es una clase de punto de entrada válida.
* Le has dicho al comando java una clase que no es una clase de punto de entrada.
* La clase de punto de entrada es incorrecta; consulte Clases de punto de entrada para obtener más información.

1 - Desde Java 8 y versiones posteriores, el comando java asignará de manera útil un separador de nombres de archivo ("/" o "") a un punto ("."). Sin embargo, este comportamiento no está documentado en las páginas del manual.

2 - Un caso realmente oscuro es si copia y pega un comando de un documento formateado en el que el editor de texto ha utilizado un "histe largo" en lugar de un guión normal.
