# El Operador De Concatenación De String (+)
El símbolo + puede significar tres operadores distintos en Java:

* Si no hay operando antes del +, entonces es el operador Plus unario.
* Si hay dos operandos, y ambos son numéricos, entonces es el operador de adición binario.
* Si hay dos operandos, y al menos uno de ellos es una cadena, entonces es el operador binario de concatenación.

En el caso simple, el operador de concatenación une dos cadenas para dar una tercera cadena. Por ejemplo:
```java
String s1 = "Un String";
String s2 = "Esto es " + s1; // s2 contiene "Esto es un String"
```
Cuando uno de los dos operandos no es una cadena, se convierte en una cadena de la siguiente manera:

* Un operando cuyo tipo es un tipo primitivo se convierte como si llamara a `toString()` en el valor de la caja.
* Un operando cuyo tipo es un tipo de referencia se convierte llamando al método `toString()` del operando.
Si el operando es `null`, o si el método `toString()` devuelve `null`, entonces se utiliza el literal de cadena "`null`" en su lugar.

Por ejemplo:
```java
int one = 1;
String s3 = "One is " + one;            // s3 contiene "One is 1" 
String s4 = null + " is null";          // s4 contiene "null is null" 
String s5 = "{1} is " + new int[]{1};   // s5 contiene algo como 
                                        // "{1} is [I@xxxxxxxx"
```
La explicación del ejemplo s5 es que el método toString() en los tipos de matriz se hereda de `java.lang.Object`,
y el comportamiento es producir una cadena que consiste en el nombre del tipo y el código hash de identidad del objeto.

El operador de concatenación se especifica para crear un nuevo objeto String,
excepto en el caso de que la expresión sea una expresión constante.
En este último caso, la expresión se evalúa en el tipo de compilación,
y su valor de tiempo de ejecución es Equivalente a una String literal.
Esto significa que no hay una sobrecarga de tiempo de ejecución para dividir una cadena larga literal como esta:
```java
String typing = "The quick brown fox " +
                "jumped over the " +
                "lazy dog"; // constant expression
```
### Optimización y Eficiencia
Como se señaló anteriormente, con la excepción de las expresiones constantes,
**cada** expresión de **concatenación de String crea un nuevo objeto** `String`. Considera este código:
```java
public String stars(int count){
    String res= "";
    for(int i=0; i<count; i++){
        res=res+"*";
    }
    return res;
}
```
En el método anterior, cada iteración del bucle creará una nueva cadena que es un carácter más largo que la iteración anterior.
Cada concatenación copia todos los caracteres de las cadenas de operando para formar la nueva cadena.
Por lo tanto, las estrellas (N):

* Crea N nuevos objetos String y tira todos, pero el último,
* copia N * (N + 1) / 2 caracteres, y
* Generar O(N^2) bytes de basura.

Esto es muy caro para el gran N.
De hecho, cualquier código que concatena cadenas en un bucle puede tener este problema.
Una mejor manera de escribir esto sería la siguiente:
```java
public String stars(int count) {
    // Crea un constructor de cadenas con capacidad 'count' 
    StringBuilder sb = new StringBuilder(count);
    for (int i = 0; i < count; i++) {
        sb.append("*");
    }
    return sb.toString();
}
```
Idealmente, deberías establecer la capacidad del StringBuilder, pero si esto no es práctico,
la clase aumentará automáticamente la matriz de respaldo que el constructor utiliza para contener caracteres.
(Nota: la implementación amplía la matriz de respaldo exponencialmente.
Esta estrategia mantiene esa cantidad de copia de caracteres en un O(N) en lugar de O(N^2).)

Algunas personas aplican este patrón a todas las concatenaciones de cadenas.
Sin embargo, esto es innecesario porque el **JLS(Java Language Specification)** 
permite a un compilador Java optimizar las concatenaciones de cadenas dentro de una sola expresión.
Por ejemplo:
```java
String s1 = ...;
String s2 = ...;
String test = "Hello " + s1 + ". Welcome to " + s2 + "\n";
```
Normalmente será optimizado por el compilador de bytecode para algo como esto;
```java
StringBuilder tmp = new StringBuilder();
tmp.append("Hello ")
tmp.append(s1 == null ? "null" + s1);
tmp.append("Welcome to ");
tmp.append(s2 == null ? "null" + s2);
tmp.append("\n");
String test = tmp.toString();
```
(El compilador JIT puede optimizarlo aún más si puede deducir que s1 o s2 no pueden ser nulos).
Pero tenga en cuenta que esta optimización solo está permitida dentro de una sola expresión.

En resumen, si le preocupa la eficiencia de las concatenaciones de cadenas:

* Haga una optimización manual si está haciendo una concatenación repetida en un bucle (o similar).
* No optimize a mano una sola expresión de concatenación.