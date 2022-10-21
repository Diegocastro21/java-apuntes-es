# Documentación Del Paquete

Es posible crear documentación a nivel de paquete en Javadocs utilizando un archivo llamado package-info.java.
Este archivo debe tener el formato de la siguiente manera. Espacios en blanco y asteriscos principales opcionales,
normalmente presentes en cada línea por razones de formato.

```java
/**
 * Package documentation goes here; any documentation before the first period will
 * be used as a summary.
 *
 * It is common practice to leave a blank line between the summary and the rest
 * of the documentation; use this space to describe the package in as much detail
 * as is appropriate.
 *
 * Inline tags such as {@code code here}, {@link reference.to.other.Documentation},
 * and {@literal text here} can be used in this documentation.
 */
package com.example.foo;
// The rest of the file must be empty.
```

En el caso anterior, debe poner este archivo`package-info.java` dentro de la carpeta del paquete Java `com.example.foo`.