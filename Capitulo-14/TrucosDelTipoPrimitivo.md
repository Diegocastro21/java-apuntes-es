# Hoja De Trucos De Tipos Primitivos
Tabla que muestra el rango de tamaño y valores de todos los tipos primitivos:

| tipo de dato | Representación numérica | Rango de valores                                                            | Valor predeterminado |
|--------------|-------------------------|-----------------------------------------------------------------------------|----------------------|
| boolean      | n/a                     | false y true                                                                | false                |
| byte         | 8-bit                   | -27 a 27 - 1  <br/> -128 a +127                                             | 0                    |
| short        | 16-bit                  | -215 a 215 - 1 <br/> -31,768 a +32,767                                      | 0                    |
| int          | 32-bit                  | -231 a 231 -1 <br/>-2,147,483,648 a +2,147,483,647                          | 0                    |
| long         | 64-bit                  | -263 a 263 -1 <br/> -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807  | 0L                   |
| float        | 32-bit punto flotante   | 1.401298464e-45 a 3.402823466e+38 (positivo o negativo)                     | 0.0F                 |
| double       | 64-bit punto flotante   | 4.94065645841246544e-324d a 1.79769313486231570e+308d (positivo o negativo) | 0.0D                 |
| char         | 16-bit Sin firmar       | 0 a 216 -1<br/>0 a 65,535                                                   | 0                    |

Notas:

1. La especificación del lenguaje Java exige que los tipos integrales firmados (`byte` a `long`) utilicen la representación binaria de dos complementos, y los tipos de coma flotante utilicen representaciones de coma flotante binarias estándar IEE 754.

2. Java 8 y versiones posteriores proporcionan métodos para realizar operaciones aritméticas sin signo en `int` y `long`. Si bien estos métodos permiten que un programa trate los valores de los tipos respectivos como no firmados, los tipos siguen siendo tipos firmados.

3. Los puntos flotantes más pequeños que se muestran arriba son subnormales; es decir, tienen menos precisión que un valor normal. Los números normales más pequeños son 1.175494351e−38 y 2.2250738585072014e−308

4. Un `char` representa convencionalmente una unidad de código Unicode / UTF-16.

5. Aunque un `boolean` contiene solo un poco de información, su tamaño en la memoria varía dependiendo del Java
Implementación de la máquina virtual (ver tipo booleano).


