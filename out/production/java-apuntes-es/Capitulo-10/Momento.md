# Instant
Representa un instante en el tiempo.
Se puede pensar como una envoltura alrededor de una marca de tiempo de Unix.
```java
Instant now = Instant.now();
Instant epoch1 = Instant.ofEpochMilli(2);
Instant epoch2 = Instant.parse("1970-01-01T00:00:00Z");
System.out.println(java.time.temporal.ChronoUnit.MICROS.between(epoch2, epoch1)); // 2000
```