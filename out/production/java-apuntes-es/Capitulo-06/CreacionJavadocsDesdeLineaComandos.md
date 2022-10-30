# Creación de Javadocs desde la línea de comandos

## Documentación Del Codigo Java
La documentación para el código java a menudo se genera usando javadoc. Javadoc fue
creado por Sun Microsystems con el propósito de generar documentación API en formato HTML a partir del código
fuente java. El uso del formato HTML da la comodidad de poder hacer hipervínculos
a documentos relacionados.

Muchos IDE proporcionan soporte para generar HTML a partir de Javadocs automáticamente; algunas herramientas de
compilación (Maven y Gradle, por ejemplo) también tienen complementos que pueden manejar la creación de HTML.

Sin embargo, estas herramientas no son necesarias para generar el HTML de Javadoc; esto se puede hacer utilizando
la herramienta javadoc de línea de comandos.

El uso más básico de la herramienta es:

```java
javadoc JavaFile.java
```

Que generará HTML a partir de los comentarios de Javadoc en JavaFile.java.

Un uso más práctico de la herramienta de línea de comandos, que leerá recursivamente todos los archivos java en
`package.name`, creará documentación para `package.name` y todos los subpaquetes, y colocará el HTML generado en el
`docs-directory` es:

```java
javadoc -d [docs-directory] -subpackages -sourcepath [source-directory] [package.name]
```