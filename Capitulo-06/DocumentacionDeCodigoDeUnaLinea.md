# Documentación Del Código En Línea

Además del código de documentación de Javadoc, se puede documentar en línea.

Los comentarios de una sola línea se inician con // y pueden colocarse después de una declaración en la misma línea, pero no antes.

```java
public void method() { //single line comment
someMethodCall(); //single line comment after statement 

}
```

Los comentarios de varias líneas se definen entre /* y */. Pueden abarcar varias líneas e incluso pueden colocarse entre las declaraciones.

```java
public void method(Object object) { 
    /*
        multi
        line
        comment 
    */
    object/*inner-line-comment*/.method(); 
}
     
```

JavaDocs es una forma especial de comentarios de varias líneas, comenzando con /**.

Como demasiados comentarios en línea pueden disminuir la legibilidad del código, deben usarse escasamente en caso de que el código no sea
Lo suficientemente autoexplicativo o la decisión de diseño no es obvia.

Un caso de uso adicional para los comentarios de una sola línea es el uso de TAG, que son palabras clave cortas basadas en convenciones. Algunos entornos de desarrollo reconocen ciertas convenciones para tales comentarios individuales. Ejemplos comunes son:

```java

    //TODO
    //FIXME
```
O emitir referencias, es decir, para Jira
```java
//PRJ-1234
```
