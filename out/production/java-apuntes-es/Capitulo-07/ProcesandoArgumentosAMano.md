# Procesando Argumentos A Mano
Cuando la sintaxis de la línea de comandos de una aplicación es simple, es razonable hacer el argumento de comando

Procesando completamente en código personalizado.

En este ejemplo, presentaremos una serie de estudios de casos sencillos.
En cada caso, el código producirá mensajes de error si los argumentos son inaceptables, y luego llamará a `System.exit(1)`
para decirle al shell que el comando ha fallado. 
(Asumiremos en cada caso que el código Java se invoca utilizando un envoltorio cuyo nombre es **"myapp"**).

### Un comando sin argumentos
En este estudio de caso, el comando no requiere argumentos. El código ilustra que `args.length` nos da el número de argumentos de línea de comandos.
```java
public class Main {
    public static void main(String[] args) {
        if (args.length > 0) {
            System.err.println("usage: myapp");
            System.exit(1);
        }
        // Run the application
        System.out.println("It worked");
    }
}
```

### Un Comando Con Dos Argumentos
En este estudio de caso, el comando requiere precisamente dos argumentos.
```java
public class Main {
    public static void main(String[] args) {
        if (args.length != 2) {
            System.err.println("usage: myapp <arg1> <arg2>");
            System.exit(1);
        }
        // Run the application
        System.out.println("It worked: " + args[0] + ", " + args[1]);
    }
}
```

Tenga en cuenta que si nos olvidamos de comprobar `args.length`,
el comando se bloquearía si el usuario lo ejecutaba con muy pocos argumentos de línea de comandos.

### Un comando con opciones de "bandera" y al menos un argumento

En este estudio de caso, el comando tiene un par de opciones de bandera (opcionales) y requiere al menos un argumento después de las opciones.

```java
package tommy; 
public class Main {
    public static void main(String[] args) { 
        boolean feelMe = false;
        boolean seeMe = false;
        int index;
        loop: for (index = 0; index < args.length; index++) { String opt = args[index];
                switch (opt) {
                case "-c":
                    seeMe = true;
                    break;
                case "-f":
                    feelMe = true;
                    break; 
                default:
                    if (!opts.isEmpty() && opts.charAt(0) == '-') {
                        error("Unknown option: '" + opt + "'");
                    }
                    break loop; 
                }
            }
            if (index >= args.length) {
                error("Missing argument(s)");
            }
            // Run the application
            // ...
    }
    private static void error(String message) { 
        if (message != null) {
            System.err.println(message);
        }
        System.err.println("usage: myapp [-f] [-c] [ <arg> ...]");
        System.exit(1);
    }
}
```
Como puede ver, el procesamiento de los argumentos y opciones se vuelve bastante engorroso si la sintaxis del comando es complicada.
Es recomendable utilizar una biblioteca de **"command line parsing"**; vea los otros ejemplos.