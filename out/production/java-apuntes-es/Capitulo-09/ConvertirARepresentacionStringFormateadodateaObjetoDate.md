# Convertir La Representación De Cadena Formateada Del date a Date Object

Este método se puede utilizar para convertir una representación de cadena con formato de una fecha en un objeto Date.
```java
/**
 * Parses the date using the given format.
 *
 * @param formattedDate the formatted date string
 * @param dateFormat the date format which was used to create the string.
 * @return the date
 */
public static Date parseDate(String formattedDate, String dateFormat) { 
        Date date = null;
        SimpleDateFormat objDf = new SimpleDateFormat(dateFormat); 
        try {
        date = objDf.parse(formattedDate); 
        } catch (ParseException e) {
        // Haz lo que sea necesario, con excepción.
        }
        return date; 
}
```