# Floating-point literals
Los literales de punto flotante proporcionan valores que se pueden usar cuando se necesita una instancia `float` o `double`.
Hay tres tipos de literales de coma flotante.

* Formas decimales simples 
* Formas decimales en escala 
* Formas hexadecimales

(Las reglas de sintaxis de JLS combinan las dos formas decimales en una sola forma. Los tratamos por separado para facilitar su explicación.)

Hay distintos tipos literales para los literales `float` y `double`, expresados usando sufijos. Los diversos formularios utilizan letras para expresar diferentes cosas. Estas letras no distinguen entre mayúsculas y minúsculas.

### Formas decimales simples

La forma más simple de literal de coma flotante consiste en uno o más dígitos decimales y un punto decimal (.)
y un sufijo opcional (f, F, d o D). El sufijo opcional le permite especificar que el literal es un valor `float` (f o F) o 
`double` (d o D). El valor predeterminado (cuando no se especifica ningún sufijo) es `double`.

Por ejemplo:
```java
0.0 // Esto denota cero
.0 // Esto tambien denota cero
0. // Esto tambien denota cero
3.14159 // Esto denota Pi, preciso (¡aproximadamente!) 5 decimales.
1.0F // Un literal `float`
1.0D // Un literal `double`. (`double` es el valor predeterminado si no se da ningún sufijo)
```
De hecho, los dígitos decimales seguidos de un sufijo también son un literal de coma flotante.
```java
1F // Significa lo mismo que 1.0F
```

El significado de un literal decimal es el número de coma flotante IEEE que está más cerca del número real matemático 
de precisión infinita denotado por la forma decimal de coma flotante.
Este valor conceptual se convierte en una representación binaria de coma flotante IEEE utilizando la ronda a la más cercana.
(La semántica precisa de la conversión decimal se especifica en los javadocs para `Double.valueOf(String)` y `Float.valueOf(String)`,
teniendo en cuenta que hay diferencias en las sintaxis numéricas).

### Formas decimales en escala

Las formas decimales en escala consisten en decimales simples con una parte exponente introducida por una E o e, y 
seguida de un entero con signo. La parte exponente es una mano corta para multiplicar la forma decimal por una potencia de diez,
como se muestra en los siguientes ejemplos.
También hay un sufijo opcional para distinguir los literales `float` y `double`.
Estos son algunos ejemplos:
```java
1.0E1 // Esto Significa 1.0 x 10^1 ... or 10.0 (double)
1E-1D // Esto Significa 1.0 x 10^(-1) ... or 0.1 (double)
1.0e10f // Esto Significa 1.0 x 10^(10) ... or 10000000000.0 (float)
```
El tamaño de un literal está limitado por la representación (`float` o `double`).
Es un error de compilación si el factor de escala da como resultado un valor que es demasiado grande o demasiado pequeño.

### Formas Hexadecimales

A partir de Java 6, es posible expresar literales de coma flotante en hexadecimal.
La forma hexadecimal tiene una sintaxis análoga a las formas decimales simples y en escala con las siguientes diferencias:

1. Cada literal de coma flotante hexadecimal comienza con un cero (0) y luego con una x o X.
2. Los dígitos del número (¡pero no la parte exponente!) También incluyen los dígitos hexadecimales de la a-f y
Sus equivalentes en mayúsculas.
3. El exponente es obligatorio y se introduce por la letra p (o P) en lugar de una e o E. El exponente
Representa un factor de escalado que es una potencia de 2 en lugar de una potencia de 10.

Estos son algunos ejemplos:
```java
0x0.0p0f // Esto es cero expresado en la forma hexadecimal (`float`) 
0xff.0p19 // Esto es 255.0 x 2^19 (`double`)
```
Consejo: dado que las formas hexadecimales de coma flotante no son familiares para la mayoría de los programadores de Java,
es recomendable usarlas con moderación.

### Subrayados

A partir de Java 7, se permiten guiones bajos dentro de las cadenas de dígitos en las tres formas de literal de coma flotante.
Esto también se aplica a las partes "exponentes". Consulte Uso de guiones bajos para mejorar la legibilidad.

### Casos especiales

Es un error de compilación si un literal de coma flotante denota un número que es demasiado grande o demasiado pequeño para representarlo
en la representación seleccionada; es decir, si el número se desbordaría a +INF o -INF, o se desbordaría a 0,0. Sin embargo,
es legal que un literal represente un número desnormalizado distinto de cero.

La sintaxis literal de coma flotante no proporciona representaciones literales para los valores especiales IEEE 754,
como los valores INF y NaN.
Si necesita expresarlos en código fuente, la forma recomendada es usar las constantes definidas por `java.lang.Float` y 
`java.lang.Double`;
por ejemplo, `Float.NaN`, `Float.NEGATIVE_INFINITY` y `Float.POSITIVE_INFINITY`.