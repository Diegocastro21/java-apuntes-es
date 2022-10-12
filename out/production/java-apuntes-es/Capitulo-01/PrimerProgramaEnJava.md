# Creando Nuestro primer programa en Java  

Crea un nuevo archivo en tu editor de texto o IDE llamado
`
HolaMundo.java
`
Y Luego pega este bloque de codigo en el archivo y guardelo
```java
public class HolaMundo {
    public static void main(String [] args){
        System.out.println("Hola Mundo!");
    }
}
```
Salida:
```
Hola Mundo!
```

**Nota:** Para que Java reconozca esto como una `public class` (Y no lanze un Error de Compilacion), el Nombre
del archivo debe ser el mismo que el de la clase(HolaMundo en este ejemplo) con la extension .java.
También debería haber el modificador de acceso public antes de este.

Las Convenciones de Nomenclatura o "Naming Conventions" Recomiendan que las clases Java comiencen con un Caracter en Mayúscula
en formato camello, en el que la primera letra de cada palabra va en mayúscula Las convenciones recomiendan
no usar guiones bajos ( _ ) ni signos de dólar ( $ ).

El compilador generará entonces un archivo de bytecode llamado `HolaMundo.class` que puede ser ejecutado en
la **máquina virtual Java (JVM)**. El compilador del lenguaje de programación Java, **javac**, lee los archivos fuente
escritos en el lenguaje de programación Java y los compila en archivos de clase bytecode.
Opcionalmente, el compilador también puede procesar las anotaciones encontradas en los archivos fuente y de 
la clase utilizando **la API Pluggable de procesamiento de anotaciones**.
El compilador es una herramienta de línea de comandos, pero también puede invocarse mediante la **Java Compiler API**.

###### Hemos codificado y construido de manera correcta nuestro primer programa en java.