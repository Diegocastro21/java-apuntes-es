# Intro

LocalTime es una clase inmutable y a prueba de hilos, utilizada para representar el tiempo,
a menudo vista como hora-min-seg. 
El tiempo se representa a una precisión de nanosegundos.
Por ejemplo, el valor "13:45.30.123456789" se puede almacenar en un LocalTime.

Esta clase no almacena ni representa una fecha o zona horaria.
En su lugar, es una descripción de la hora local que se ve en un reloj de pared.
No puede representar un instante en la línea de tiempo sin información adicional,
como un desplazamiento o una zona horaria. Esta es una clase basada en valores,
el método igual debe usarse para las comparaciones.

### Fields

MAX - El máximo compatible con LocalTime, '23:59:59.999999999'.MIDNIGHT, MIN, NOON

### Métodos estáticos importantes

* Now()
* now(Clock clock)
* now(ZoneId zone)
* parse(CharSequence text)

### Métodos de instancia importantes

* isAfter(LocalTime other)
* isBefore(LocalTime other)
* minus(TemporalAmount amountToSubtract)
* minus(long amountToSubtract, TemporalUnit unit)
* plus(TemporalAmount amountToAdd)
* plus(long amountToAdd, TemporalUnit unit)
```java
ZoneId zone = ZoneId.of("Asia/Kolkata");
LocalTime now = LocalTime.now();
LocalTime now1 = LocalTime.now(zone);
LocalTime then = LocalTime.parse("04:16:40");
```
La diferencia de tiempo se puede calcular de cualquiera de las siguientes maneras
```java
long timeDiff = Duration.between(now, now1).toMinutes();
long timeDiff1 = java.time.temporal.ChronoUnit.MINUTES.between(now2, now1);
```
También puedes añadir/substraer horas, minutos o segundos de cualquier objeto de LocalTime.

* minusHours(long hoursToSubtract)
* minusMinutes(long hoursToMinutes)
* minusNanos(long nanosToSubtract)
* minusSeconds(long secondsToSubtract)
* plusHours(long hoursToSubtract)
* plusMinutes(long hoursToMinutes)
* plusNanos(long nanosToSubtract)
* plusSeconds(long secondsToSubtract)
```java
now.plusHours(1L);
now1.minusMinutes(20L);
```