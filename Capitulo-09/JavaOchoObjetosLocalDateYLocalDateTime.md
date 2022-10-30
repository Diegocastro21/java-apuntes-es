# Objetos Java 8 LocalDate y LocalDateTime

Los objetos Date y LocalDate no se pueden convertir exactamente entre sí, ya que un objeto Date representa tanto un día y
una hora específicos, mientras que un objeto LocalDate no contiene información de hora o zona horaria.
Sin embargo, puede ser útil convertir entre los dos si solo te importa la información de la fecha real y no la información de la hora.

### Creando LocalDate
```java
// Creando un Date default
LocalDate lDate = LocalDate.now();

// Creando un Date a partir de Valores
lDate = LocalDate.of(2017, 12, 15);

// Creando una Date a partir de un String
lDate = LocalDate.parse("2017-12-15");

// Creando un Date a partir de un la zone
LocalDate.now(ZoneId.systemDefault());
```

### Creando un LocalDateTime
```java
// Creando una DateTime por default
LocalDateTime lDateTime = LocalDateTime.now();

// Creando un DateTime a partir de valores
lDateTime = LocalDateTime.of(2017, 12, 15, 11, 30);

// Creando DateTime a partir de un String
lDateTime = LocalDateTime.parse("2017-12-05T11:30:30");

// Creando DateTime a partir de una Zone
LocalDateTime.now(ZoneId.systemDefault());
```

### LocalDate A Date Y Vice-versa

```java
Date date = Date.from(Instant.now());
ZoneId defaultZoneId = ZoneId.systemDefault();

// Date a LocalDate
LocalDate localDate = date.toInstant().atZone(defaultZoneId).toLocalDate();
        
// LocalDate a Date
Date.from(localDate.atStartOfDay(defaultZoneId).toInstant());
```

### LocalDateTime A Date Y Vice-versa
```java
Date date = Date.from(Instant.now());
ZoneId defaultZoneId = ZoneId.systemDefault();

// Date to LocalDateTime
LocalDateTime localDateTime = date.toInstant().atZone(defaultZoneId).toLocalDateTime();

// LocalDateTime to Date
Date out = Date.from(localDateTime.atZone(defaultZoneId).toInstant());
```