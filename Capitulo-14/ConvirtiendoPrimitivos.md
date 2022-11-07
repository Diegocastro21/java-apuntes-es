# Conversión De Primitivos
En Java, podemos convertir entre valores enteros y valores de coma flotante.
Además, dado que cada carácter corresponde a un número en la codificación Unicode,
los tipos de `char` se pueden convertir hacia y desde los tipos enteros y de coma flotante.
El `boolean` es el único tipo de datos primitivo que no se puede convertir a o desde ningún otro tipo de datos primitivo.

Hay dos tipos de conversiones: widening conversión y narrowing conversión.

Una (widening conversión ) o conversión de ampliación es cuando un valor de un tipo de datos se convierte en un valor de otro tipo de datos que ocupa
Más bits que el primero. No hay ningún problema de pérdida de datos en este caso.

En consecuencia, una (narrowing conversión) 0 conversión de estrechamiento es cuando un valor de un tipo de datos 
se convierte en un valor de otro tipo de datos que ocupa menos bits que el primero.
En este caso, puede producirse una pérdida de datos.

Java realiza conversiones de ampliación automáticamente.
Pero si desea realizar una (narrowing conversión) conversión de estrechamiento (si está seguro de que no se producirá ninguna pérdida de datos), 
entonces puede obligar a Java a realizar la conversión utilizando una construcción de lenguaje conocida como `cast`.

### Widening Conversion:
```java
 int a = 1;
double d = a; // Conversión válida a doble, no se necesita cast (widening)
```
### Narrowing Conversion:
```java
double d = 18.96
int b = d;          // Conversión no válida a int, lanzará un error en tiempo de compilación
int b = (int) d;    // Conversión válida a int, pero el resultado está truncado (se redondea hacia abajo)
                    // Esto es fundición a presión (type-casting)
                    // ahora, b = 18
```