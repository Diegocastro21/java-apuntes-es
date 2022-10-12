# Utilizacion De Los Tipos Numeros Basicos

```java
public static void main(String[] args) {

        char char1 = 1, char char2 = 2;
        short short1 = 1, short short2 = 2;
        int int1 = 1; int int2 = 2;
        float float1 = 1.0f;
        float float2 = 2.0f;
        
```
`char1 = char1 + char2;`
No se puede convertir un int a char

`short1 = short1 + short2;` No se puede convertir de un int a short.

`int1 = char1 + char2;` char es convertido a int.

`int1 = short1 + short2;` short is convertido a int.

`int1 = char1 + short2;` char y short son convertidos a int.

`float1 = short1 + float2;` short en convertido a float.

`int1 = int1 + int2;` int no ha cambiado.
