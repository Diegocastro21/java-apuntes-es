# Calcular Diferencias Entre 2 LocalDates

Usa `LocalDate` y `ChronoUnit`:
```java
LocalDate d1 = LocalDate.of(2022, 5, 2);
LocalDate d2 = LocalDate.of(2022, 5, 18);
```
Ahora, ya que el método `between` el enumerador `ChronoUnit` toma 2 Temporales como parámetros para que pueda pasar sin 
problemas las instancias de `LocalDate`
```java
long dias = ChronoUnit.DAYS.between(d1, d2);
System.out.println(dias); // 16
```