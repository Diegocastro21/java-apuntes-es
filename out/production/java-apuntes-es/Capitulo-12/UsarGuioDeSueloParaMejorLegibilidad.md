# Usar El Guión De Suelo Para Mejorar La Legibilidad

Desde Java 7 ha sido posible utilizar uno o más guiones bajos (_) para separar grupos de dígitos en un número primitivo
literal para mejorar su legibilidad.

Por ejemplo, estas dos declaraciones son equivalentes:
>Version ≥ Java SE 7
```java
int i1 = 123456;
int i2 = 123_456;
System.out.println(i1 == i2); // true
```
Esto se puede aplicar a todos los literales de números primitivos, como se muestra a continuación:
```java
byte color = 1_2_3;
short yearsAnnoDomini= 2_016;
int socialSecurtyNumber = 999_99_9999;
long creditCardNumber = 1234_5678_9012_3456L;
float piFourDecimals = 3.14_15F;
double piTenDecimals = 3.14_15_92_65_35;
```
Esto también funciona usando prefijos para bases binarias, octales y hexadecimales:
```java
short binary= 0b0_1_0_1;
int octal = 07_7_7_7_7_7_7_7_0; long hexBytes = 0xFF_EC_DE_5E;
```
Hay algunas reglas sobre los guiones bajos que **prohíben** su colocación en los siguientes lugares:

* Al principio o al final de un número (por ejemplo, `_123` o `123_` no son válidos)
* Adyacente a un punto decimal en un literal de coma flotante (Por Ejemplo, `1._23` o `1_.23` no son válidos)
* Antes de un sufijo F o L (por ejemplo, `1.23_F` o `9999999_L` no son válidos)
* En posiciones donde se espera una cadena de dígitos (por ejemplo, `0_xFFFF` no es válido)
