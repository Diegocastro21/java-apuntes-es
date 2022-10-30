# LocalTime

Para usar solo la parte de la hora de una fecha, use LocalTime. Puedes crear una instancia de un objeto LocalTime de un par de maneras

1. `LocalTime time = LocalTime.now();`
2. `time = LocalTime.MIDNIGHT;`
3. `time = LocalTime.NOON;`
4. `time = LocalTime.of(12, 12, 45);`

`LocalTime` también tiene un método toString integrado que muestra el formato muy bien.
```java
System.out.println(time);
```
También puede obtener, sumar y restar horas, minutos, segundos y nanosegundos del objeto LocalTime, es decir,
```java
time.plusMinutes(1);
time.getMinutes();
time.minusMinutes(1);
```
Puedes convertirlo en un objeto Date con el siguiente código:
```java
LocalTime lTime = LocalTime.now();
Instant instant = lTime.atDate(LocalDate.of(A_YEAR, A_MONTH, A_DAY)).
        atZone(ZoneId.systemDefault()).toInstant();
Date time = Date.from(instant);
```
Esta clase funciona muy bien dentro de una clase de temporizador para simular un despertador.
