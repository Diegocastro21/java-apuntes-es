# Formato de Date y Time
Antes de Java 8, había clases `DateFormat` y `SimpleDateFormat` en el paquete `java.text` y este
código heredado se continuará utilizando durante algún tiempo.

Sin embargo, Java 8 ofrece un enfoque moderno para manejar el formato y el análisis.

En el formato y el análisis, primero pasas un objeto `String` a `DateTimeFormatter` y, a su vez, lo usas para formatear o analizar.

```java
import java.time.*;
import java.time.format.*;
class DateTimeFormat {
    public static void main(String[] args) {

        //Parsing
        String pattern = "d-MM-yyyy HH:mm";
        DateTimeFormatter dtF1 = DateTimeFormatter.ofPattern(pattern);

        LocalDateTime ldp1 = LocalDateTime.parse("2014-03-25T01:30"), //Default format
                    ldp2 = LocalDateTime.parse("15-05-2016 13:55",dtF1); //Custom format

        System.out.println(ldp1 + "\n" + ldp2); //Se imprimirá en formato predeterminado

        // Formateo
        DateTimeFormatter dtF2 = DateTimeFormatter.ofPattern("EEE d, MMMM, yyyy HH:mm");
        
        DateTimeFormatter dtF3 = DateTimeFormatter.ISO_LOCAL_DATE_TIME;
        
        LocalDateTime ldtf1 = LocalDateTime.now();
        
        System.out.println(ldtf1.format(dtF2) +"\n"+ldtf1.format(dtF3));
    }

}
```
Salida:
```java
2014-03-25T01:30
2016-05-15T13:55
Sun 30, October, 2022 13:20
2022-10-30T13:20:14.433539
```

Un aviso importante, en lugar de usar patrones personalizados, es una buena práctica usar formateadores predefinidos. 
Tu código se ve más claro y el uso de ISO8061 definitivamente te ayudará a largo plazo.