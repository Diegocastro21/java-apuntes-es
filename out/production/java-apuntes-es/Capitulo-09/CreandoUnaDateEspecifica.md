# Crear Una Fecha Específica

Si bien la clase Java Date tiene varios constructores, notarás que la mayoría están obsoletas. La única forma aceptable de crear una instancia de Date directamente es usando el constructor vacío o pasando un largo (número de milisegundos desde la hora base estándar). Ninguno de los dos es útil a menos que esté buscando la fecha actual o ya tenga otra instancia de fecha a mano.

Para crear una nueva fecha, necesitarás una instancia de calendario. Desde allí puedes configurar la instancia del calendario en la fecha que necesites.
```java
Calendar c = Calendar.getInstance();
```
Esto devuelve una nueva instancia de calendario establecida en la hora actual. El calendario tiene muchos métodos para cambiar su fecha
Y el tiempo o establecerlo directamente. En este caso, lo fijaremos en una fecha específica.
```java
c.set(1974, 6, 2, 8, 0, 0);
Date d = c.getTime();
```
El método `getTime` devuelve la instancia de fecha que necesitamos. Tenga en cuenta que los métodos de conjunto de
calendario solo establecen uno o más campos, no los establecen todos. Es decir, si estableces el año, los otros campos
permanecen sin cambios.

### Trampa

En muchos casos, este fragmento de código cumple su propósito, pero tenga en cuenta que no se definen dos partes importantes de la fecha/hora.

* Los parámetros (`1974, 6, 2, 8, 0, 0`) se interpretan dentro de la zona horaria predeterminada, definida en otro lugar,
* Los milisegundos no se establecen en cero, sino que se llenan desde el reloj del sistema en el momento en que se crea
la instancia del calendario.