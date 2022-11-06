# String literals
Los literales de String proporcionan la forma más conveniente de representar los valores de cadena en el código fuente
de Java. Un literal de cadena consta de:

* Un carácter de doble coma (") de apertura.
* Cero o más otros caracteres que no son ni una comillas dobles ni un carácter de salto de línea.(Un carácter de barra invertida (\) altera el significado de los caracteres posteriores; consulte Escapar secuencias en literales.)
* Un carácter de doble comillas de cierre.

Por ejemplo:

```java
"Hello world"  // Un literal que denota una String de 11 caracteres
""             // Un literal que denota una String vacía (de longitud cero)
"\""           // Un literal que denota una String que consiste en una
               //     Carácter de doble cita
"1\t2\t3\n"    // Otro literal con secuencias de escape
```
Tenga en cuenta que un literal de una sola String puede no abarcar varias líneas de código fuente.
Es un error de compilación para que se produzca un salto de línea (o el final del archivo de origen)
antes de la doble coma de cierre de un literal. Por ejemplo:
```java
"Jello world    // Compilation error (at the end of the line!)
```

### Long strings
Si necesita una cadena que sea demasiado larga para caber en una línea,
la forma convencional de expresarla es dividirla en múltiples literales y usar el operador de concatenación (+)
para unir las piezas. Por ejemplo:
```java
String practicaEscritura = "El zorro marrón rápido " +
                            "Saltó " +
                            "El perro perezoso"
```
Una expresión como la anterior que consiste en literales de cadena y + satisface los requisitos para ser una expresión 
constante. Eso significa que la expresión será evaluada por el compilador y representada en tiempo de
ejecución por un solo objeto `String`.

### Internado de literales de cadena
Cuando el archivo de clase que contiene literales de cadena es cargado por la JVM,
los objetos de String correspondientes son internados por el sistema de tiempo de ejecución.
Esto significa que un literal de String utilizado en varias clases no ocupa más espacio que si se usara en una clase.

Para obtener más información sobre la internación y el grupo de cadenas,
consulte el ejemplo de almacenamiento de grupos de cadenas y heap en el tema Cadenas.