# Java Options

El comando java admite una amplia gama de opciones:

* Todas las opciones comienzan con un solo guión o signo menos (-): la convención GNU/Linux de uso -- para "largo" Las opciones no son compatibles.
* Las opciones deben aparecer antes de que se reconozca el argumento `<classname>` o `-jar <jarfile>`. Cualquier argumento después de ellos se tratará como un argumento que se pasará a la aplicación Java que se está ejecutando.
* Las opciones que no comienzan con -X o -XX son opciones estándar. Puedes confiar en todas las implementaciones de Java para admitir cualquier opción estándar.
* Las opciones que comienzan con -X son opciones no estándar y se pueden retirar de una versión de Java a la siguiente. 
* Las opciones que comienzan con -XX son opciones avanzadas y también se pueden retirar.

### Configuración de las propiedades del sistema con -D

La opción `-D<propiedad>=<valor>` se utiliza para establecer una propiedad en el objeto **Properties** del sistema. Este parámetro se puede repetir para establecer diferentes propiedades.

### Memory, Stack and Garbage Collector options

Las principales opciones para controlar los tamaños de montón y pila están documentadas en Setting the Heap, PermGen y Stack sizes.

### Habilitar y desactivar las aserciones

Las opciones -ea y -da, respectivamente, activan y desactivan la comprobación de la Java **assert**:

* Toda la comprobación de aserción está desactivada de forma predeterminada.
* El `-ea` permite comprobar todas las afirmaciones
* El `-ea:<nombre del paquete>...` permite comprobar las aserciones en un paquete y en todos los subpaquetes.
* El `-ea:<nombre de clase>...` permite comprobar las aserciones en una clase.
* La opción `-da` desactiva la comprobación de todas las afirmaciones
* El `-da:<nombre del paquete>...`ndeshabilita la comprobación de las aserciones en un paquete y todos los subpaquetes. 
* El `-da:<nombre de clase>...` desactiva la comprobación de las aserciones en una clase.
* La opción `-esa` permite comprobar todas las clases del sistema.
* La opción `-dsa` desactiva la comprobación de todas las clases del sistema.

Las opciones se pueden combinar. Por ejemplo.

```clickhouse
$ # Enable all assertion checking in non-system classes
$ java -ea -dsa MyApp
    
$ # Enable assertions for all classes in a package except for one.
$ java -ea:com.wombat.fruitbat... -da:com.wombat.fruitbat.Brickbat MyApp
```

Tenga en cuenta que habilitar la comprobación de aserciones puede alterar el comportamiento de una programación Java.

* Es responsable que la solicitud sea más lenta en general.
* Puede hacer que los métodos específicos tarden más en ejecutarse, lo que podría cambiar la sincronización de los subprocesos en una aplicación multiprocesos.
* Puede introducir relaciones fortuitas que pueden hacer que desaparezcan las anomalías de la memoria.
* Una declaración de `assert` incorrectamente implementada podría tener efectos secundarios no deseados.

**Seleccionado el VM Type**

Las opciones `-client` y `-server` le permiten seleccionar entre dos formas diferentes de la máquina virtual HotSpot:

* El formulario "cliente" está sintonizado para las aplicaciones de usuario y ofrece un inicio más rápido.
* El formulario "servidor" está sintonizado para aplicaciones de larga duración. Se tarda más tiempo en capturar las estadísticas durante el "calentamiento" de la JVM, lo que permite al compilador JIT hacer un mejor trabajo de optimización del código nativo.

De forma predeterminada, la JVM se ejecutará en modo de 64 bits si es posible, dependiendo de las capacidades de la plataforma. Las opciones `-d32` y `-d64` le permiten seleccionar el modo explícitamente.

1 - Consulta el manual oficial del comando java. A veces, una opción estándar se describe como "sujeta a cambios".