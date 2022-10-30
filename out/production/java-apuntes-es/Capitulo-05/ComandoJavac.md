# El Comando 'javac' 

### Ejemplo Simple

Asumimos que la clase `"HolaMundo.java"` contiene el siguiente codigo:
```java
public class HolaMundo{
    public static void main(String[] args) {
        System.out.println("Hola Mundo!");
    }
}
```
(Para una explicación del código anterior, consulte Primeros pasos con el lenguaje Java).

Podemos compilar el archivo anterior usando este comando:
```
$ javac HolaMundo.java
```
Esto genera un archivo llamado "HolaMundo.class", Que podemos ejecutar de la siguiente manera:
```java
$ java HolaMundo
Hola Mundo!
```
Los puntos clave a tener en cuenta de este ejemplo son:

1. El nombre de archivo de origen "HolaMundo.java" **debe coincidir con el nombre de la clase en el archivo de origen**... que es HolaMundo. **Si no coinciden, obtendrá un error de compilación**.
2. El nombre de archivo de bytecode "HolaMundo.class" corresponde al nombre de la clase. **Si cambiaras el nombre** de "HolaMundo.class", **obtendrías un error cuando intentaras ejecutarlo.**
3. Al ejecutar una aplicación Java usando java, proporciona el nombre de la clase, **NO** el nombre de archivo de bytecode.

### Ejemplo con paquetes

La mayoría de los códigos Java prácticos utilizan paquetes para organizar el espacio de nombres para las clases y
reducir el riesgo de colisión accidental de nombres de clase.

Si quisiéramos declarar la clase HolaMundo en un paquete llamado com.ejemplo,
el "HolaMundo.java" contendría la siguiente fuente Java:
```java
package com.ejemplo;

public class HolaMundo{
    public static void main(String[] args) {
        System.out.println("Hola Mundo!");
    }
}
```
Este codigo fuente
este archivo de código fuente debe almacenarse en un árbol de directorios cuya estructura corresponde a la denominación del paquete.
```java
. # El directorio actual (De este Ejemplo) |
----com 
    |
    ----ejemplo
        |
        ----HolaMundo.java
```
podemos compilar el archivo anterior utilizando este comando:
```java
$ javac com/ejemplo/HolaMundo.java
```
Esto produce un archivo llamado `"com/ejemplo/HolaMundo.class";` Es decir, después de la compilación, la estructura de
los archivos debería tener el siguiente aspecto:
```java
. # El directorio actual (De este Ejemplo) |
----com 
    |
    ----ejemplo
        |
        ----HolaMundo.java
        ----HolaMundo.class
```
Podemos ejecutar la aplicación de la siguiente manera:
```java
$ java com.ejemplo.HolaMundo
Hola Mundo!
```
Los puntos adicionales a tener en cuenta de este ejemplo son:

1. La estructura del directorio debe coincidir con la estructura del **nombre del paquete**.
2. Cuando ejecutas la clase, se debe proporcionar **el nombre completo de la clase**; es decir, "com.ejemplo.HolaMundo" no
"HolaMundo".
3. No tienes que compilar y ejecutar código Java desde el directorio actual. Solo lo estamos haciendo aquí por
Ilustración.

### Compilar varios archivos a la vez con "javac".

Si su aplicación consta de varios archivos de código fuente (¡y la mayoría lo hace!) Puedes compilarlos de uno en uno.
Alternativamente, puede compilar varios archivos al mismo tiempo enumerando los nombres de ruta:
```java
$ javac Foo.java Bar.java
```
O utilizando la funcionalidad de comodín de nombre de archivo de su el shell o (intérprete de órdenes)de la línea de comandos
```
$ javac *.java
$ javac com/ejemplo/*.java
$ javac */**/*.java  
```
Esto compilará todos los archivos fuente de Java en el directorio actual,
en el directorio "com/ejemplo" y recursivamente en los directorios secundarios, respectivamente.
Una tercera alternativa es proporcionar una lista de nombres de archivo de origen (y opciones de compilador) como un archivo.
Por ejemplo:
```java
javac @sourcefiles
```
donde el archivo `sourcefiles` contiene:
```java
Foo.java
Bar.java
com/ejemplo/HolaMundo.java
```
Nota: compilar código como este es apropiado para pequeños proyectos de una sola persona y para programas de una sola vez.
Más allá de eso, es recomendable seleccionar y utilizar la Java build tool.
Alternativamente, la mayoría de los programadores utilizan un IDE de Java (p. ej. **NetBeans**, **eclipse**, **IntelliJ IDEA**)
que ofrece un compilador integrado y una construcción incremental de "proyectos".

### Opciones de "javac" de uso común

Aquí hay algunas opciones para el comando javac que probablemente te sean útiles

* La opción **-d** establece un directorio de destino para escribir los archivos".class".
* La opción **-sourcepath** establece una ruta de búsqueda de código fuente.
* La opción **-cp** o **-classpath** establece la ruta de búsqueda para encontrar clases externas y previamente compiladas. Para obtener más información sobre la ruta de clase y cómo especificarla, consulte el tema de la ruta de clase.
* La opción **-version** imprime la información de la versión del compilador.

En un ejemplo separado se describirá una lista más completa de las opciones del compilador.
