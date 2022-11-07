# Los operadores de incremento/decremento (++/--)
Las variables se pueden incrementar o disminuir en 1 utilizando los operadores `++` y `--`, respectivamente.

Cuando los operadores `++` y `--` siguen las variables,
se llaman post-incremento y post-decremento, respectivamente.
```java
int a = 10;
a++; // Es ahora igual a 11
a--; // Es ahora igual a 10 de nuevo
```
Cuando los operadores ++ y -- preceden a las variables,
las operaciones se llaman pre-incremento y pre-decremento, respectivamente.
```java
int x = 10;
--x; // x ahora equivale a 9
++x; // x ahora equivale a 10
```
Si el operador precede a la variable, el valor de la expresión es el valor de la variable después de haber sido incrementado o decrementado.
Si el operador sigue a la variable, el valor de la expresión es el valor de la variable antes de ser incrementada o decrementada.
```java
int x=10;
System.out.println("x=" + x + " x=" + x++ + " x=" + x); // Salidas x=10 x=10 x=11 
System.out.println("x=" + x + " x=" + ++x + " x=" + x); // Salidas x=11 x=12 x=12 
System.out.println("x=" + x + " x=" + x-- + " x=" + x); // Salidas x=12 x=12 x=11 
System.out.println("x=" + x + " x=" + --x + " x=" + x); // Salidas x=11 x=10 x=10
```
Tenga cuidado de no sobrescribir los incrementos o decrementos posteriores.
Esto sucede si utiliza un operador post-in/decremento al final de una expresión que se reasigna a la propia variable in/decremented.
El incremento/decremento no tendrá ningún efecto. A pesar de que la variable del lado izquierdo se incrementa correctamente,
su valor se sobrescribirá inmediatamente con el resultado evaluado previamente del lado derecho de la expresión:
```java
int x = 0;
x = x++ + 1 + x++;  // x = 0 + 1 + 1
                    // No hagas esto, el último incremento no tiene efecto (¡error!) 
System.out.println(x); // Imprime 2 (no 3!)
```
Correctamente:
```java
int x = 0;
x = x++ + 1 + x;        // Evalua a x = 0 + 1 + 1
x++;                    // Agrega 1 
System.out.println(x);  // Imprime 3
```