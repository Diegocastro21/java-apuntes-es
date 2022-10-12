# Casting de Numeros Primitivos

Los numeros primitivos pueden ser casteados de dos maneras. **Implicit Casting**
se produce cuando el tipo de origen tiene un rango menor que el tipo de destino

```java
// Casteo Implicito
byte variable_byte = 35;
short variable_short = variableByte;
int variable_int = variable_short;
long variable_long = variable_int;
float variable_float = variable_long;
double variable_double = variable_float;
```
El casteo explícito tiene que hacerse cuando el tipo de origen tiene mayor alcance que el tipo de destino.

```java
//Casteo Explicito
double variable_double = 35.0d;
float variable_float = (float) variable_double;
long variable_long = (long) variable_float;
int variable_int = (int) variable_long;
short variable_short = (short) variable_int;
byte variable_byte = (byte) variable_short;
```
Cuando se convierte numeros primitivos con decimales o de punto flotante como (float, double) en numeros primitivos enteros,
el número se redondea hacia abajo