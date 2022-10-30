# Manipulaciones De Date Simples

Obtén la fecha actual.
```java
LocalDate.now()
```
Consigue la fecha de ayer.
```java
LocalDate y = LocalDate.now().minusDays(1);
```
Consigue la fecha de mañana
```java
LocalDate t = LocalDate.now().plusDays(1);
```
Obtén una fecha específica.
```java
LocalDate t = LocalDate.of(1974, 6, 2, 8, 30, 0, 0);
```
Además de los métodos `plus` y `minus`, hay un conjunto de métodos "con" que se pueden utilizar para establecer un
Campo en una instancia de `LocalDate`.

```java
LocalDate.now().withMonth(6);
```
El ejemplo anterior devuelve una nueva instancia con el mes establecido en junio
(esto difiere de java.util.Date donde setMonth se indexó en 0 haciendo el 5 de junio).

Debido a que las manipulaciones de LocalDate devuelven instancias inmutables de LocalDate,
estos métodos también pueden estar encadenados.
```java
LocalDate ld = LocalDate.now().plusDays(1).plusYears(1);
```
Esto nos daría la fecha de mañana dentro de un año.