# Convertir Un String En Date

`Parse()` de la clase `SimpleDateFormat` ayuda a convertir un **String** pattern en un objeto **Date**.
```java
DateFormat dateFormat = DateFormat.getDateInstance(DateFormat.SHORT, Locale.US);
String dateStr = "02/25/2004"; // input String
Date date = null;

try {
    date = dateFormat.parse(dateStr);
} catch (ParseException e) {
    throw new RuntimeException(e);
}

System.out.println(date.getYear()); // 104
```
Hay 4 estilos diferentes para el formato de texto,
`SHORT`, `MEDIUM` (este es el predeterminado), `LONG` y `FULL`, todos los cuales dependen de la configuración regional. 
Si no se especifica ninguna configuración regional, se utiliza la configuración regional predeterminada del sistema.

| Estilo | Locale.US            | Locale.France      |
|--------|----------------------|--------------------|
| SHORT  | 8/20/08              | 20/08/08           |
| MEDIUM | Jun 20, 2008         | 20 juin 2008       |
| LONG   | June 20, 2008        | 20 juin 2008       |
| FULL   | Monday,June 20, 2008 | Lundi 20 juin 2008 |

