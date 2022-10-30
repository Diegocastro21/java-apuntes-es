# Una Salida Date Básica

Usando el siguiente código con la cadena de formato `yyyy/MM/dd hh:mm.ss`, recibiremos la siguiente salida:

> 2022/10/29 19:14:20

```java
// Definir el formato a utilizar
String formatString = "yyyy/MM/dd hh:mm.ss";

// Obtener un objeto de fecha actual
Date date = Calendar.getInstance().getTime(); 

// Crea un formateador
SimpleDateFormat simpleDateFormat = new SimpleDateFormat(formatString);

// Formatea la fecha
String formattedDate = simpleDateFormat.format(date);

// Imprimelo
System.out.println(formattedDate);

// Versión de una sola línea de todo el código anterior
System.out.println(new SimpleDateFormat("yyyy/MM/dd hh:mm.ss").format(Calendar.getInstance().getTime()));
```
