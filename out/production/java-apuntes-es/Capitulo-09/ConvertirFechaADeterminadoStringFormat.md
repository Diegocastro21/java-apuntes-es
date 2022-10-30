# Convertir La Fecha A Un Determinado String Format

`Format()` de la clase `SimpleDateFormat` ayuda a convertir un objeto `Date` en un determinado objeto `String` de
formato utilizando la _pattern string_ suministrada.
```java
Date hoy = new Date();

SimpleDateFormat dateFormat = new SimpleDateFormat("dd-MMM-yy"); //pattern is specified here
System.out.println(dateFormat.format(hoy)); //29-Oct-22
```
Los patrones se pueden aplicar de nuevo usando `applyPattern()`
```java
dateFormat.applyPattern("dd-MM-yyyy");
System.out.println(dateFormat.format(hoy)); //29-10-2022
        
dateFormat.applyPattern("dd-MM-yyyy HH:mm:ss E");
System.out.println(dateFormat.format(hoy)); //29-10-2022 19:38:11 Sat
```
> Nota: Aquí mm (pequeña letra m) denota minutos y MM (M mayúscula) denota mes. Preste atención al formatear años: mayúscula "Y" (Y) indica la "semana del año", mientras que "y" (y) mayúsculas indica el año.