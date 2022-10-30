# Ejecutar Un Archivo JAR Ejecutable

Los archivos JAR ejecutables son la forma más sencilla de ensamblar el código Java en un solo archivo que se puede ejecutar.

Suponiendo que tenga un archivo JAR ejecutable con el nombre de ruta **<jar-path>**, debería poder ejecutarlo de la siguiente manera:
```java
java -jar <jar-path>
```
Si el comando requiere argumentos de línea de comandos, añádelos después de **<jar-path>**. Por ejemplo:
```java
java -jar <jar-path> arg1 arg2 arg3
```
Si necesita proporcionar opciones adicionales de JVM en la línea de comandos de java, deben ir antes de la opción `-jar`.
Tenga en cuenta que una opción `-cp` / `-classpath `se ignorará si utiliza `-jar`. La ruta de clase de la aplicación está 
determinada por el manifiesto del archivo JAR.

