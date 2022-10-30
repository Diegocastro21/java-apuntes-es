# Modificación del Time
Puedes añadir horas, minutos, segundos y nanosegundos:
```java
LocalTime time = LocalTime.now();
LocalTime addHours = time.plusHours(5); // Agregar 5 horas
LocaLTime addMinutes = time.plusMinutes(15) // Agregar 15 minutos
LocalTime addSeconds = time.plusSeconds(30) // Agregar 30 segundos
LocalTime addNanoseconds = time.plusNanos(150_000_000) // Agregar 150.000.000ns (150ms)
```