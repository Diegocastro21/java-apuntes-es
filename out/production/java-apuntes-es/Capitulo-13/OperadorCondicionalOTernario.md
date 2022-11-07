# El Operador Condicional (? :) O Ternario
Sintaxis:
> {Condición para evaluar} **?** {Declaracion-Ejecutada-en-true} **:** {declaracion-ejecutada-en-false}

Como se muestra en la sintaxis, el operador condicional (también conocido como operador ternario)
utiliza el **?** **(Signo de interrogación)** y **: (Dos Puntos)** caracteres para permitir una expresión condicional de dos posibles resultados.
Se puede utilizar para reemplazar bloques más largos si otros para devolver uno de los dos valores basados en la condición. 
```java
resultado = condicionDePrueba ? valor1 : valor2
```
Es equivalente a
```java
if (condicionDePrueba) {
    resultado = valor1;
} else {
    resultado = valor2;
}
```
Se puede leer como **"Si la condición de prueba es verdadera, establezca el resultado en valor1; de lo contrario, establezca el resultado en valor2"**.

Por ejemplo:
```java
// Obtener valor absoluto usando el operador condicional o Ternario
a = -10;
int valorAbso = a < 0 ? -a : a;
System.out.println("abs = " + valorAbso); // Imprime "abs = 10"
```
Es equivalente a
```java
// Obtener valor absoluto usando el if/else loop
a = -10;
int valorAbso;
if (a < 0) {
    valorAbso = -a; 
} else {
    valorAbso = a;
}
System.out.println("abs = " + absValue); // Imprime "abs = 10"
```

### Uso común
Puedes usar el operador condicional para asignaciones condicionales (como la comprobación nula).
```java
String x = y != null ? y.toString() : ""; //donde y es un Objeto
```
Es equivalente a
```java
String x = "";

if (y != null) {
    x = y.toString();
}
```
Dado que el operador condicional tiene la segunda precedencia más baja, por encima de los operadores de asignación,
rara vez es necesario usar paréntesis alrededor de la condición,
pero se requiere paréntesis alrededor de toda la construcción del operador condicional cuando se combina con otros operadores:
```java
// no se necesitan paréntesis para las expresiones de las 3 partes
10 <= a && a < 19 ? b * 5 : b * 7
        
// Es requerido el parentesis
7 * (a > 0 ? 2 : 5)
```
La anidación de los operadores condicionales también se puede hacer en la tercera parte,
donde funciona más como un encadenamiento o como una declaración de `switch`.
```java
a ? "a es true" :
b ? "a se false, b se true" :
c ? "a y b son false, c es true" :
    "a, b, y c son false"

//La precedencia del operador se puede ilustrar con paréntesis:
a ? x : (b ? y : (c ? z : w))
```
**Nota a pie:**

1 - Tanto la especificación del lenguaje Java como el tutorial de Java llaman al **operador (? :)** el operador condicional.
El tutorial dice que es "también conocido como el operador **ternario**", ya que es (actualmente) el único operador ternario definido por Java.
La terminología del "Operador condicional" es consistente con C y C++ y otros lenguajes con un operador equivalente.