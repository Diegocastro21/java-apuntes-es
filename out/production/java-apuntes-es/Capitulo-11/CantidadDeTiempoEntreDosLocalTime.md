# Cantidad De Tiempo entre dos LocalTime

Hay dos formas equivalentes de calcular la cantidad de unidad de tiempo entre dos `LocalTime`:
1. a través del método hasta (`Temporal`, `TemporalUnit`) 
2. a través de `TemporalUnit.between``(``Temporal``,``Temporal``)`.
```java
import java.time.LocalTime;
import java.time.temporal.ChronoUnit;

public class AmountOfTime {
    
    public static void main(String[] args) {
        
        LocalTime start = LocalTime.of(1, 0, 0); // hour, minute, second
        LocalTime end = LocalTime.of(2, 10, 20); // hour, minute, second
        
        long halfDays1 = start.until(end, ChronoUnit.HALF_DAYS); // 0
        long halfDays2 = ChronoUnit.HALF_DAYS.between(start, end); // 0
        
        long hours1 = start.until(end, ChronoUnit.HOURS); // 1 
        long hours2 = ChronoUnit.HOURS.between(start, end); // 1
        
        long minutes1 = start.until(end, ChronoUnit.MINUTES); // 70
        long minutes2 = ChronoUnit.MINUTES.between(start, end); // 70
        
        long seconds1 = start.until(end, ChronoUnit.SECONDS); // 4220
        long seconds2 = ChronoUnit.SECONDS.between(start, end); // 4220
        
        long millisecs1 = start.until(end, ChronoUnit.MILLIS); // 4220000
        long millisecs2 = ChronoUnit.MILLIS.between(start, end); // 4220000
        
        long microsecs1 = start.until(end, ChronoUnit.MICROS); // 4220000000
        long microsecs2 = ChronoUnit.MICROS.between(start, end); // 4220000000
        
        long nanosecs1 = start.until(end, ChronoUnit.NANOS); // 4220000000000
        long nanosecs2 = ChronoUnit.NANOS.between(start, end); // 4220000000000
        
        // Usando otros ChronoUnit se lanzará UnsupportedTemporalTypeException.
        // Los siguientes métodos son ejemplos de ello.
        long days1 = start.until(end, ChronoUnit.DAYS);
        long days2 = ChronoUnit.DAYS.between(start, end);
        // Exception in thread "main" java.time.temporal.UnsupportedTemporalTypeException: Unsupported unit: Days
        // at java.base/java.time.temporal.ChronoUnit.between
    } 
}
```