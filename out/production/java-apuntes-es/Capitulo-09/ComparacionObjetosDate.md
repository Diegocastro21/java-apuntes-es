# Comparación De Objetos Date

### Calendar, Date, and LocalDate
Version < Java SE 8
### Antes, Después De los metodos compareTo and equals 
```java
//Uso del calendario y Objetos Date
final Date today = new Date();
final Calendar calendar = Calendar.getInstance();
calendar.set(1995, Calendar.NOVEMBER, 1, 0, 0, 0);
Date birthdate = calendar.getTime();
final Calendar calendar2 = Calendar.getInstance();
calendar2.set(1995, Calendar.NOVEMBER, 1, 0, 0, 0);
Date samebirthdate = calendar2.getTime();

//Ejemplo con Before
System.out.printf("Is %1$tF before %2$tF? %3$b%n", today, birthdate,
Boolean.valueOf(today.before(birthdate)));
System.out.printf("Is %1$tF before %1$tF? %3$b%n", today, today,
Boolean.valueOf(today.before(today)));
System.out.printf("Is %2$tF before %1$tF? %3$b%n", today, birthdate,
Boolean.valueOf(birthdate.before(today)));

//Ejemplo con After
System.out.printf("Is %1$tF after %2$tF? %3$b%n", today, birthdate,
Boolean.valueOf(today.after(birthdate)));
System.out.printf("Is %1$tF after %1$tF? %3$b%n", today, birthdate,
Boolean.valueOf(today.after(today)));
System.out.printf("Is %2$tF after %1$tF? %3$b%n", today, birthdate,
Boolean.valueOf(birthdate.after(today)));

//Ejemplo con Compare
System.out.printf("Compare %1$tF to %2$tF: %3$d%n", today, birthdate,
Integer.valueOf(today.compareTo(birthdate)));
System.out.printf("Compare %1$tF to %1$tF: %3$d%n", today, birthdate,
Integer.valueOf(today.compareTo(today)));
System.out.printf("Compare %2$tF to %1$tF: %3$d%n", today, birthdate,
Integer.valueOf(birthdate.compareTo(today)));

//Ejemplo con Equal
System.out.printf("Is %1$tF equal to %2$tF? %3$b%n", today, birthdate,
Boolean.valueOf(today.equals(birthdate)));
System.out.printf("Is %1$tF equal to %2$tF? %3$b%n", birthdate, samebirthdate,
Boolean.valueOf(birthdate.equals(samebirthdate)));
System.out.printf("Because birthdate.getTime() -> %1$d is different from samebirthdate.getTime() -> %2$d, there are millisecondes!%n",
Long.valueOf(birthdate.getTime()), Long.valueOf(samebirthdate.getTime()));

//Clear ms from calendars
calendar.clear(Calendar.MILLISECOND);
calendar2.clear(Calendar.MILLISECOND);
birthdate = calendar.getTime();
samebirthdate = calendar2.getTime();
System.out.printf("Is %1$tF equal to %2$tF after clearing ms? %3$b%n", birthdate, samebirthdate,
Boolean.valueOf(birthdate.equals(samebirthdate)));
```
Version ≥ Java SE 8
### isBefore, isAfter, compareTo and equals methods
```java
//Uso de LocalDate
final LocalDate now = LocalDate.now();
final LocalDate birthdate2 = LocalDate.of(2017, 10, 23);
final LocalDate birthdate3 = LocalDate.of(2017, 9, 20);

//Las horas, los minutos, el segundo y el nanosegundo también se pueden configurar con otra clase LocalDateTime
//LocalDateTime.of(year, month, dayOfMonth, hour, minute, second, nanoOfSecond);

//Ejemplo isBefore
System.out.printf("Is %1$tF before %2$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(now.isBefore(birthdate2)));
System.out.printf("Is %1$tF before %1$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(now.isBefore(now)));
System.out.printf("Is %2$tF before %1$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(birthdate2.isBefore(now)));

//Ejemplo con isAfter
System.out.printf("Is %1$tF after %2$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(now.isAfter(birthdate2)));
System.out.printf("Is %1$tF after %1$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(now.isAfter(now)));
System.out.printf("Is %2$tF after %1$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(birthdate2.isAfter(now)));

//Ejemplo con compareTo
System.out.printf("Compare %1$tF to %2$tF %3$d%n", now, birthdate2,
        Integer.valueOf(now.compareTo(birthdate2)));
System.out.printf("Compare %1$tF to %1$tF %3$d%n", now, birthdate2,
        Integer.valueOf(now.compareTo(now)));
System.out.printf("Compare %2$tF to %1$tF %3$d%n", now, birthdate2,
        Integer.valueOf(birthdate2.compareTo(now)));

//Ejemplo con Equals
System.out.printf("Is %1$tF equal to %2$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(now.equals(birthdate2)));
System.out.printf("Is %1$tF to %2$tF? %3$b%n", birthdate2, birthdate3,
        Boolean.valueOf(birthdate2.equals(birthdate3)));

//Ejemplo con isEqual
System.out.printf("Is %1$tF equal to %2$tF? %3$b%n", now, birthdate2,
        Boolean.valueOf(now.isEqual(birthdate2)));
System.out.printf("Is %1$tF to %2$tF? %3$b%n", birthdate2, birthdate3,
        Boolean.valueOf(birthdate2.isEqual(birthdate3)));
```
### Comparación de Date antes de Java 8

Antes de Java 8, las fechas se podían comparar utilizando las clases `java.util.Calendar` y `java.util.Date`.
La clase de fecha ofrece 4 métodos para comparar fechas:

* after(Date when)
* before(Date when)
* compareTo(Date anotherDate)
* equals(Object obj)

los métodos `after`, `before`, `compareTo` y `equals` comparan los valores devueltos por el método getTime() para cada fecha.
El método compareTo devuelve un entero positivo.

* El Valor mayor que 0 : cuando la fecha está después del argumento Date 
* El Valor mayor que 0 : cuando la fecha está antes del argumento Date 
* El valor es igual a 0 : cuando la fecha es igual al argumento Date

Los resultados `equals` pueden ser sorprendentes como se muestra en el ejemplo porque los valores, como los milisegundos,
no se inicializan con el mismo valor si no se dan explícitamente.

### Desde Java 8

Con Java 8, un nuevo objeto para trabajar con Date está disponible `java.time.LocalDate`. LocalDate implementa `ChronoLocalDate`,
la representación abstracta de una fecha en la que la Cronología, o sistema de calendario, se puede conectar.

Para tener la precisión de la fecha y hora, se debe usar el objeto `java.time.LocalDateTime`. `LocalDate` y `LocalDateTime` utilizan el mismo nombre de método para comparar.

Comparar fechas usando un `LocalDate` es diferente de usar `ChronoLocalDate` porque la cronología o el sistema de calendario no se tienen en cuenta el primero.

Debido a que la mayoría de las aplicaciones deberían usar `LocalDate`, `ChronoLocalDate` no está incluido en los ejemplos. Más información aquí.

> La mayoría de las aplicaciones deben declarar firmas de métodos, campos y variables como LocalDate, no como esta interfaz [ChronoLocalDate].


LocalDate tiene 5 métodos para comparar fechas:

* isAfter(ChronoLocalDate other)
* isBefore(ChronoLocalDate other)
* isEqual(ChronoLocalDate other)
* compareTo(ChronoLocalDate other)
* equals(Object obj)

En el caso del parámetro `LocalDate`, `isAfter`, `isBefore`, `isEqual`, `equals` y `compareTo` utilizar ahora este método:
```java
int compareTo0(LocalDate otherDate) {
    int cmp = (year - otherDate.year);
    if (cmp == 0) {
        cmp = (month - otherDate.month);
        if (cmp == 0) {
            cmp = (day - otherDate.day);
        }
    }
    return cmp; 
}
```

`Equals` a la comprobación del método si la referencia del parámetro es igual a la fecha primero, mientras que `isEqual`
llama directamente a `compareTo0`. 

En el caso de otra instancia de clase de `ChronoLocalDate`, las fechas se comparan utilizando el `Epoch Day`. El Día de la Época
Count es un simple recuento incremental de días en los que el día 0 es 1970-01-01 (ISO).