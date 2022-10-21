# Documentación De Campos

Todos los comentarios de Javadoc comienzan con un comentario en bloque seguido de un
asterisco (/**) y terminan cuando el comentario en bloque lo hace (*/). Opcionalmente,
cada línea puede comenzar con espacios en blanco arbitrarios y un solo asterisco; estos se
ignoran cuando se generan los archivos de documentación.

```java
/**
 * Fields can be documented as well.
 *
 * As with other javadocs, the documentation before the first period is used as a
 * summary, and is usually separated from the rest of the documentation by a blank
 * line.
 *
 * Documentation for fields can use inline tags, such as:
 * {@code code here}
 * {@literal text here}
 * {@link other.docs.Here}
 *
 * Field documentation can also make use of the following tags:
 *
 * @since 2.1.0
 * @see some.other.class.Documentation
 * @deprecated Describe why this field is outdated
 */
public static final String CONSTANT_STRING = "foo";
```