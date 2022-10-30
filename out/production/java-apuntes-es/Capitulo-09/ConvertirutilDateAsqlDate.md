# Convertir java.util.Date a java.sql.Date

La conversión de `java.util.Date` a `java.sql.Date` suele ser necesaria cuando un objeto Date debe escribirse en una base de datos.

`java.sql.Date` es un envoltorio alrededor del valor de milisegundo y es utilizado por `JDBC` para identificar un tipo `SQL DATE`

En el siguiente ejemplo, utilizamos el constructor `java.util.Date()`, que crea un objeto Date y lo inicializa para representar
el tiempo al milisegundo más cercano. Esta fecha se utiliza en el método `convert(java.util.Date utilDate)` para devolver un objeto `java.sql.Date`

Ejemplo:
```java
public class UtilToSqlConversion {
    
    public static void main(String args[]) {
        
        java.util.Date utilDate = new java.util.Date();
        System.out.println("java.util.Date is : " + utilDate);
        java.sql.Date sqlDate = convert(utilDate);
        System.out.println("java.sql.Date is : " + sqlDate);
        DateFormat df = new SimpleDateFormat("dd/MM/YYYY - hh:mm:ss");
        System.out.println("dateFormated date is : " + df.format(utilDate));
        
    }
    private static java.sql.Date convert(java.util.Date uDate) {
        java.sql.Date sDate = new java.sql.Date(uDate.getTime());
        return sDate;
    } 
}
```
Salida:
```java
java.util.Date is : Sat Oct 29 19:11:43 COT 2022
java.sql.Date is : 2022-10-29
dateFormated date is : 29/10/2022 - 07:11:43
```

java.util.Date tiene información de fecha y hora, mientras que java.sql.Date solo tiene información de fecha