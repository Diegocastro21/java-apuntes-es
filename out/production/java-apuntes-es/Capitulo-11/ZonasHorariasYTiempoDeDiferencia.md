# Zonas Horarias Y Su Tiempo De Diferencia
```java
import java.time.LocalTime;
import java.time.ZoneId;
import java.time.temporal.ChronoUnit;
public class Test {
    public static void main(String[] args) {

        ZoneId zone1 = ZoneId.of("Europe/Berlin");
        ZoneId zone2 = ZoneId.of("Brazil/East");

        LocalTime now = LocalTime.now();
        LocalTime now1 = LocalTime.now(zone1);
        LocalTime now2 = LocalTime.now(zone2);

        System.out.println("Current Time : " + now);
        System.out.println("Berlin Time : " + now1);
        System.out.println("Brazil Time : " + now2);

        long minutesBetween = ChronoUnit.MINUTES.between(now2, now1);
        System.out.println("Minutes Between Berlin and Brazil : " + minutesBetween + "mins");
    }
}
```
Salida:
```java
Current Time : 14:26:30.225132
Berlin Time : 20:26:30.225159
Brazil Time : 16:26:30.226078
Minutes Between Berlin and Brazil : 239mins
```