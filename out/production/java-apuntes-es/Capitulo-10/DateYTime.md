# Date y Time

Fecha y hora sin información de zona horaria
```java
LocalDateTime dateTime = LocalDateTime.of(2020, Month.JULY, 27, 8, 0);
LocalDateTime now = LocalDateTime.now();
LocalDateTime parsed = LocalDateTime.parse("2020-07-27T07:00:00");
```

Fecha y hora con información de zona horaria
```java
ZoneId zoneId = ZoneId.of("UTC+2");
ZonedDateTime dateTime = ZonedDateTime.of(2020, Month.JULY, 27, 7, 0, 0, 235, zoneId);
ZonedDateTime composition = ZonedDateTime.of(localDate, localTime, zoneId);
ZonedDateTime now = ZonedDateTime.now(); // Zona horaria predeterminada
ZonedDateTime parsed = ZonedDateTime.parse("2020-07-27T07:00:00+01:00[Europe/Stockholm]");
```
Fecha y hora con información de compensación (es decir, no se tienen en cuenta los cambios de horario de verano)
```java
ZoneOffset zoneOffset = ZoneOffset.ofHours(2);
OffsetDateTime dateTime = OffsetDateTime.of(2020, 7, 27, 7, 0, 0, 235, zoneOffset);
OffsetDateTime composition = OffsetDateTime.of(localDate, localTime, zoneOffset);
OffsetDateTime now = OffsetDateTime.now(); // Desplazamiento tomado del ZoneId predeterminado
OffsetDateTime parsed = OffsetDateTime.parse("2016-07-27T07:00:00+02:00");
```