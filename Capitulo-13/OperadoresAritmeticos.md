# Los Operadores Aritméticos (+, -, *, /, %)
El lenguaje Java proporciona 7 operadores que realizan aritmética en valores enteros y de coma flotante.

* Hay más de dos operadores `+` :
  * El operador de suma binaria añade un número a otro. (También hay un operador binario + que realiza la concatenación de cadenas. Eso se describe en un ejemplo separado.)
  * El operador unario plus no hace nada más que activar la promoción numérica (ver más abajo)
* Hay dos operadores `-` :
  * El operador de resta binaria resta un número de otro.
  * El operador menos unario es equivalente a restar su operando de cero.
* El operador de multiplicación binario (`*`) multiplica un número por otro.
* El operador de división binaria (`/`) divide un número por otro.
* El operador binario Remainder (`%`) calcula el resto cuando un número se divide por otro.

  1. Esto a menudo se conoce incorrectamente como el operador "módulo". "Remainder" es el término que utiliza el JLS.
  "Módulo" y "Remainder" no son lo mismo.

### Tipos de operando y resultado, y promoción numérica

Los operadores requieren operandos numéricos y producen resultados numéricos.
Los tipos de operando pueden ser cualquier tipo numérico primitivo
(es decir, `byte`, `short`, `char`, `int`, `long`, `float` o `double`) 
o cualquier tipo de envoltura numérica definida en java.lang;
es decir, (`Byte`, `Character`, `Short`, `Integer`, `Long`, `Float` o `Double`.

El tipo de resultado se determina en función de los tipos del operando o operandos, de la siguiente manera:

* Si cualquiera de los operandos es `double` o `Double`, entonces el tipo de resultado es `double`.
* De lo contrario, si cualquiera de los operandos es `float` o `Float`, entonces el tipo de resultado es `float`.
* De lo contrario, si cualquiera de los operandos es `long` o `Long`, entonces el tipo de resultado es `long`.
* De lo contrario, el tipo de resultado es `int`. Esto cubre los operandos de `bytes`, `short` y `char`, así como `int`.

El tipo de resultado de la operación determina cómo se realiza la operación aritmética y cómo se manejan los operandos

* Si el tipo de resultado es `double`, los operandos se promueven a `double` y la operación se realiza utilizando aritmética de coma flotante IEE 754 de 64 bits (binaria de double precisión).
* Si el tipo de resultado es `float`, los operandos se promueven a `float`, y la operación se realiza utilizando aritmética de punto flotante IEE 754 de 32 bits ( binario de precisión única).
* Si el tipo de resultado es `long`, los operandos se promueven a `long` y la operación se realiza utilizando aritmética de enteros binarios de doble firmado de 64 bits.
* Si el tipo de resultado es `int`, los operandos se promocionan a `int`, y la operación se realiza utilizando aritmética de enteros binarios de doble firmado de 32 bits.

La promoción se realiza en dos etapas:

* Si el tipo de operando es un tipo de envoltura, el valor del operando se desempaquetan a un valor del tipo primitivo correspondiente.
* Si es necesario, el tipo primitivo se promueve al tipo requerido:
  * La promoción de enteros a `int` o `long` es sin pérdidas.
  * La promoción del `float` al `double` es sin pérdidas.
  * La promoción de un entero a un valor de coma flotante puede provocar una pérdida de precisión.
  La conversión se realiza utilizando la semántica de "redondo a más cercano" de IEE 768.

### El significado de la división

El operador `/` divide el operando izquierdo n (el dividendo) y el operando derecho d (el divisor) y produce el resultado q (el cociente).

La división de enteros de Java gira hacia cero. La sección 15.17.2 de JLS especifica el comportamiento de la división de enteros de Java de la siguiente manera:
>El cociente producido para los operandos `n` y `d` es un valor entero q cuya magnitud es lo más grande posible mientras satisface `|d ⋅ q| ≤ |n|`.
> Además, `q` es positivo cuando `|n| ≥ |d|` y `n` y `d` tienen el mismo signo, pero `q` es negativo cuando `|n| ≥ |d|` y `n` y `d` tienen signos opuestos.

Hay un par de casos especiales:

* Si la `n` es `MIN_VALUE` y el divisor es -1, entonces se produce un desbordamiento de enteros y el resultado es `MIN_VALUE`.
No se hace ninguna excepción en este caso.
* Si `d` es 0, entonces se lanza `ArithmeticException`.

La división de coma flotante de Java tiene más casos de borde a considerar. 
Sin embargo, la idea básica es que el resultado `q` es el valor más cercano a satisfacer `d. q = n`.

La división de puntos flotantes nunca dará lugar a una excepción.
En su lugar, las operaciones que se dividen por cero dan como resultado valores `INF` y `NaN`; véase más abajo.

### El significado del Remainder o Modulo

A diferencia de C y C++, el operador restante en Java funciona con operaciones de enteros y de coma flotante.

Para los casos enteros, el resultado de un `a % b` se define como el número `r` de tal manera que `(a / b) * b + r` es igual `a`,
donde `/, *` y `+` son los operadores enteros Java apropiados. Esto se aplica en todos los casos, excepto cuando `b` es cero.
En ese caso, el resto da como resultado una `ArithmeticException`.

De la definición anterior se desprende que un `a % b` solo puede ser negativo si a es negativo,
y solo puede ser positivo si a es positivo.
Además, la magnitud de un `a % b` siempre es menor que la magnitud de `b`.

La operación de resto de punto flotante es una generalización del caso entero.
El resultado de un `a % b` es que el resto `r` se define por la relación matemática `r = a - (b ⋅ q)` donde:

* `q` es un entero,
* Es negativo solo si `a / b` es negativo y positivo solo si `a / b` es positivo, y
* Su magnitud es lo más grande posible sin exceder la magnitud del verdadero cociente matemático de `a` y `b`.

El resto de punto flotante puede producir valores de `INF` y `NaN` en casos de borde, como cuando `b` es cero;
véase más abajo. No lanzará una excepción.

Nota importante:
> El resultado de una operación de resto de coma flotante calculada por `%` **no es el mismo** que el producido por la operación de remainder o modulo definida por IEEE 754.
> El remainder o Modulo del IEEE 754 se puede calcular utilizando el método de la biblioteca `Math.IEEEremainder`.

###  Integer Overflow

Los valores enteros de Java de 32 y 64 bits están firmados y utilizan una representación binaria de doble complemento.
Por ejemplo, el rango de números representables como (32 bits) `int` -231 a +231 - 1.

Cuando sumas, restas o múltiples dos enteros de N bits (N == 32 o 64), 
el resultado de la operación puede ser demasiado grande para representarlo como un entero de N bits. 
En este caso, la operación conduce al _desbordamiento de enteros_, y el resultado se puede calcular de la siguiente manera:

* La operación matemática se realiza para dar una representación intermedia del complemento de dos del número completo. Esta representación será más grande que N bits.
* Los 32 o 64 bits inferiores de la representación intermedia se utilizan como resultado.

Cabe señalar que el desbordamiento de enteros no da lugar a excepciones bajo ninguna circunstancia.

### Valores de punto flotante INF y NAN

Java utiliza representaciones de coma flotante IEE 754 para `float` y `double`.
Estas representaciones tienen algunos valores especiales para representar valores que están fuera del dominio de los números reales:

* Los valores "infinitos" o INF denotan números que son demasiado grandes. El valor `+INF` denota números que son demasiado grandes y positivos.
El valor `-INF` denota números que son demasiado grandes y negativos.
* Los "indefinidos" / "no un número" o NaN denotan valores resultantes de operaciones sin sentido.

Los valores de INF se producen mediante operaciones flotantes que causan desbordamiento, o por división por cero.

Los valores de NaN se producen dividiendo cero por cero, o calculando cero restante cero.

Sorprendentemente, es posible realizar aritmética utilizando operandos INF y NaN sin desencadenar excepciones. Por ejemplo:

* Añadir +INF y un valor finito da +INF.
* Agregar +INF y +INF da +INF.
* Agregar +INF y -INF da NaN.
* Dividir por INF da +0.0 o -0.0.
* Todas las operaciones con uno o más operandos NaN dan NaN.

Para obtener todos los detalles, consulte las subsecciones pertinentes de JLS 15.
Tenga en cuenta que esto es en gran medida "académico". 
Para los cálculos típicos, un INF o NaN significa que algo ha salido mal;
por ejemplo, tiene datos de entrada incompletos o incorrectos, o el cálculo se ha programado incorrectamente. 

