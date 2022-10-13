# Compilación Para una Versión Diferente De Java

El lenguaje de programación Java (y su tiempo de ejecución) ha sufrido numerosos cambios desde su lanzamiento desde
su lanzamiento público inicial. Estos cambios incluyen:

* Cambios en la sintaxis y semántica del lenguaje de programación Java
* Cambios en las API proporcionadas por las bibliotecas de clases estándar de Java.
* Cambios en el conjunto de instrucciones de Java (bytecode) y el formato de archivo de clase.

Con muy pocas excepciones (por ejemplo, la palabra clave **enum**, cambios en algunas clases "internas", etc.), 
estos cambios son compatibles con versiones anteriores.

* Un programa Java que se compiló utilizando una versión anterior de la cadena de herramientas Java se ejecutará en una versión más reciente de la plataforma Java sin recompilación
* Un programa Java que se escribió en una versión anterior de Java se compilará con éxito con un nuevo compilador de Java.

### Compilando Java antiguo con un compilador más nuevo

Si necesita (re)compilar código Java más antiguo en una plataforma Java más nueva para ejecutarse en la plataforma más nueva,
generalmente no necesita dar ningún indicador de compilación especial.
En algunos casos (por ejemplo, si hubiera utilizado la enumeración como identificador), podría usar la opción -source para desactivar la nueva sintaxis.
Por ejemplo, dada la siguiente clase:
```java
public class SintaxisAntigua {
    private static int enum; // no es válido en Java 5 o posterior
}
```
lo siguiente es necesario para compilar la clase utilizando un compilador de java 5 (o posterior);
```java
$ java -source 1.4 SintaxisAntigua.java
```
### Compilación para una plataforma de ejecución más antigua

Si necesitas compilar Java para que se ejecute en una plataforma Java más antigua,
el enfoque más simple es instalar un JDK para la más antigua Versión que necesitas admitir y usar ese compilador de JDK en tus compilaciones.

También puedes compilar con un compilador Java más nuevo, pero son complicados.
En primer lugar, hay algunas condiciones previas importantes que deben cumplirse:

* El código que está compilando no debe usar construcciones de lenguaje Java que no estaban disponibles en la versión de Java a la que se dirige.
* El código no debe depender de clases, campos, métodos estándar de Java, etc. que no estaban disponibles en las plataformas más antiguas.
* Las bibliotecas de terceros de las que depende el código también deben construirse para la plataforma anterior y estar disponibles en tiempo de compilación y ejecución.

Dado que se cumplen las condiciones previas, puede recompilar código para una plataforma más antigua utilizando la opción `-target`. Por ejemplo,
```java
$ javac -target 1.4 MismaClase.java
```
Compilará la clase anterior para producir bytecodes que sean compatibles con Java 1.4 o posterior JVM.
(De hecho, la opción - source implica un -target compatible, por lo que javac -source 1.4 ... tendría el mismo efecto.
La relación entre -fuente y -objetivo se describe en la documentación de Oracle.)

Dicho esto, si simplemente usa **-target** o **-source**, seguirá compilando con las bibliotecas de clases estándar
proporcionadas por el JDK del compilador. Si no tiene cuidado, puede terminar con clases con la versión correcta de bytecode,
pero con dependencias de API que no están disponibles. La solución es usar la opción -bootclasspath. 
Por ejemplo:
```java
$ javac -target 1.4 --bootclasspath path/to/java1.4/rt.jar MismaClase.java
```
Compilará contra un conjunto alternativo de bibliotecas de tiempo de ejecución. Si la clase que se está compilando tiene
dependencias (accidentales) de bibliotecas más nuevas, esto le dará errores de compilación.