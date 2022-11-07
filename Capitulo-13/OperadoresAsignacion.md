# Los Operadores De Asignación (=, +=, -=, *=, /=, %=, <<=, >>= , >>>=, &=, |= y ^=)
El operando izquierdo de estos operadores debe ser una variable no final o un elemento de una matriz.
El operando de la derecha debe ser compatible con el operando de la izquierda.
Esto significa que los tipos deben ser los mismos,
o el tipo de operando derecho debe ser convertible al tipo de operando izquierdo por una combinación de boxeo,
desembalaje o ampliación. (Para obtener más detalles, consulte JLS 5.2.)

El significado preciso de los operadores de "operar y asignar" se especifica en JLS 15.26.2 como:
> Una expresión de asignación compuesta de la forma `E1 op= E2` es equivalente a `E1 = (T) ((E1) op (E2))`,
Donde `T` es el tipo de `E1`, excepto que E1 se evalúa solo una vez.

Tenga en cuenta que hay un tipográfico implícito antes de la asignación final.

1. `=`

El operador de asignación simple: asigna el valor del operando de la mano derecha al operando de la mano izquierda.
> Ejemplo: `c = a + b` añadirá el valor de `a + b` al valor de `c` y lo asignará a `c`

2. `+=`

El operador "añadir y asignar": 
añade el valor del operando de la mano derecha al valor del operando de la mano izquierda y asigna el resultado al operando de la mano izquierda.
Si el operando de la izquierda tiene un tipo `String`, entonces este es un operador de "concatenar y asignar".
> Ejemplo: `c += a ` es aproximadamente lo mismo que `c = c + a`

3. `-=`

El operador "sustar y asignar": resta el valor del operando derecho del valor del operando zurdo y asigna el resultado al operando zurdo.
> Ejemplo: `c -= a` es más o menos lo mismo que `c = c - a`

4. `*=`

El operador "multiplicar y asignar": multiplica el valor del operando de la mano derecha por el valor del operando de la izquierda y asigna el resultado al operando de la mano izquierda.
> Ejemplo: `c *= a` es aproximadamente lo mismo que `c = c * a`

5. `/=`

El operador "dividir y asignar": 
divide el valor del operando de la derecha por el valor del operando de la izquierda y asigna el resultado al operando de la izquierda.
> Ejemplo: `c /= a` es más o menos lo mismo que `c = c / a`

6. `%=`

El operador "modular y asignar": calcula el módulo del valor del operando de la mano derecha por el valor del operando de la mano izquierda y asigna el resultado al operando de la mano izquierda.
> Ejemplo: `c %= a` es más o menos lo mismo que `c = c % a`

7. `<<=`

El operador de "cambio de izquierda y asignación".
> Ejemplo: `c <<= 2` es más o menos lo mismo que `c = c << 2`

8. `>>=`

El operador de "cambio aritmético a la derecha y asignación".
> Ejemplo: `c >>= 2` es más o menos lo mismo que `c = c >> 2`

9. `>>>=`

El operador de "cambio lógico a la derecha y asignación".
> Ejemplo: `c >>>= 2` es aproximadamente lo mismo que `c = c >>> 2`

10. `&=`

El operador "bitwise **and** and assign".
> Ejemplo: `c &= 2` es más o menos lo mismo que `c = c & 2`

11. `|=`

El operador "bitwise **or** y asignar".
> Ejemplo: `c |= 2` es más o menos lo mismo que `c = c | 2`

12. `^=`

El operador "bitwise **exclusivo or** y asignado".
> Ejemplo: `c ^= 2` es más o menos lo mismo que `c = c ^ 2`