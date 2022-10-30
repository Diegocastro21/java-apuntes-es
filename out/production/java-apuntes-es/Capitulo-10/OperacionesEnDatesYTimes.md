# Operaciones En Dates Y Times

```java
LocalDate tomorrow = LocalDate.now().plusDays(1);
LocalDateTime anHourFromNow = LocalDateTime.now().plusHours(1);
Long daysBetween = java.time.temporal.ChronoUnit.DAYS.between(LocalDate.now(),
        LocalDate.now().plusDays(3)); // 3
Duration duration = Duration.between(Instant.now(), 
        ZonedDateTime.parse("2016-07-27T07:00:00+01:00[Europe/Stockholm]"))
```