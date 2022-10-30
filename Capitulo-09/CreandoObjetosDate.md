# Creación de objetos Date

```java
Date date = new Date();
System.out.println(date);
```
Aquí este objeto `Date` contiene la fecha y hora actuales en que se creó este objeto.

```java
Calendar calendar = Calendar.getInstance();
calendar.set(97, Calendar.OCTOBER, 21);
Date myBirthDate = calendar.getTime();
System.out.println(myBirthDate); // Sat Oct 21 19:51:44 COT 97
```
Los objetos de `Date` se crean mejor a través de una instancia de `Calendar`,
ya que el uso de los constructores de datos está obsoleto y se desaconseja. 
Para hacerlo, necesitamos obtener una instancia de la clase de `Calendar` del método de fábrica.
Luego podemos establecer el año, el mes y el día del mes usando números o, en caso de constantes de meses proporcionadas
a la clase de Calendario para mejorar la legibilidad y reducir los errores.

```java
calendar.set(97, Calendar.OCTOBER, 16, 11, 33, 33);
Date myBirthDatenTime = calendar.getTime();
System.out.println(myBirthDatenTime); // Mon Oct 16 11:33:33 COT 97
```
Junto con la fecha, también podemos pasar el tiempo en el orden de horas, minutos y segundos.