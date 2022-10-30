# Zonas Horarias Y java.util.Date

Un objeto `java.util.Date` no tiene un concepto de zona horaria.

* No hay forma de **set** una zona horaria para una fecha
* No hay forma de **change** la zona horaria de un objeto Date
* Un objeto Date creado con el constructor predeterminado `new Date()` se inicializará con la hora actual en la zona horaria predeterminada del sistema.

Sin embargo, es posible mostrar la fecha representada por el punto en el tiempo descrito por el objeto Date en una zona horaria diferente utilizando,
por ejemplo, `java.text.SimpleDateFormat`:
```java

Date date = new Date();
//Imprime la zona horaria predeterminada
System.out.println(TimeZone.getDefault().getDisplayName());
SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss"); //Nota: ¡La zona horaria no está en formato!
//Imprimir la fecha en la zona horaria original
System.out.println(sdf.format(date));
//Hora actual en Londres
sdf.setTimeZone(TimeZone.getTimeZone("Europe/London"));
System.out.println(sdf.format(date));
```

Salida:
```java
Colombia Standard Time
2022-10-30 11:45:24
2022-10-30 16:45:24
```