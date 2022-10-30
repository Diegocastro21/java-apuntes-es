# Espacios y otros caracteres especiales en los argumentos
En primer lugar, el problema de manejar espacios en los argumentos NO es en realidad un problema de Java. Más bien es un problema que debe ser manejado por el shell de comandos que está utilizando cuando ejecuta un programa Java.

Como ejemplo, supongamos que tenemos el siguiente programa simple que imprime el tamaño de un archivo:
```java
import java.io.File;
public class PrintFileSizes {
    public static void main(String[] args) {
        for (String name: args) {
        File file = new File(name);
        System.out.println("Size of '" + file + "' is " + file.size());
        }
    } 
}
```
Ahora supongamos que queremos imprimir el tamaño de un archivo cuyo nombre de ruta tiene espacios; 
por ejemplo, `/home/steve/Test File.txt`. Si ejecutamos el comando de esta manera:
```java
$ java PrintFileSizes /home/steve/Test File.txt
```
El shell no sabrá que `/home/steve/Test File.txt` es en realidad un nombre de ruta. En su lugar, pasará 2 argumentos distintos a la aplicación Java,
que intentará encontrar sus respectivos tamaños de archivo, y fallará porque los archivos con esas rutas (probablemente) no existen.

### Soluciones que utilizan un shell POSIX

Los proyectiles POSIX también incluyen sh derivados como bash y ksh. Si estás usando uno de estos shells, entonces puedes resolver el problema citando el argumento.

```java
$ java PrintFileSizes "/home/steve/Test File.txt"
```
Las comillas dobles alrededor del nombre de la ruta le dicen al shell que debe pasarse como un solo argumento. Las citas se eliminará cuando esto suceda. Hay un par de otras formas de hacer esto:
```java
$ java PrintFileSizes '/home/steve/Test File.txt'
```
Las comillas simples (directas) se tratan como comillas dobles, excepto que también suprimen varias expansiones dentro del Argumento.

```java
$ java PrintFileSizes /home/steve/Test\ File.txt
```

Una barra invertida escapa al siguiente espacio y hace que no se interprete como un separador de argumentos.

Para obtener una documentación más completa, incluidas las descripciones de cómo lidiar con otros caracteres especiales en los argumentos, consulte el tema de la cita en la documentación de Bash.

Solución para Windows

El problema fundamental para Windows es que a nivel del sistema operativo, los argumentos se pasan a un proceso secundario como una sola cadena (fuente). Esto significa que la responsabilidad final de analizar (o volver a analizar) la línea de comandos recae en cualquiera de los programas o en sus bibliotecas de tiempo de ejecución. Hay mucha inconsistencia.

En el caso de Java, para abreviar una larga historia:

* Puedes poner comillas dobles alrededor de un argumento en un comando java, y eso te permitirá pasar argumentos con espacios en ellos.
* Aparentemente, el comando java en sí está analizando la cadena de comandos, y lo hace más o menos bien. Sin embargo, cuando intenta combinar esto con el uso de SET y la sustitución de variables en un archivo por lotes, se obtiene
* Realmente complicado en cuanto a si se eliminan las comillas dobles.
* El shell cmd.exe aparentemente tiene otros mecanismos de escape; por ejemplo, duplicar las comillas dobles y usar ^ escapes.

Para obtener más detalles, consulte la documentación del archivo por lotes.