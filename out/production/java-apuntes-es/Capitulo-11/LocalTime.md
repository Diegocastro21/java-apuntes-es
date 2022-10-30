# LocalTime
| Metodo                         | Salida                                           |
|--------------------------------|--------------------------------------------------|
| `LocalTime.of(13, 12, 10)`     | 13:12:10                                         |
| `LocalTime.MIDNIGHT   `          | 00:00                                            |
| `LocalTime.NOON  `               | 12:00                                            |
| `LocalTime.now() `               | Hora actual del reloj del sistema                |
| `LocalTime.MAX  `                | La hora local máxima admitida 23:59:59.999999999 |
| `LocalTime.MIN  `                | La hora local Minima admitida 00:00              |
| `LocalTime.ofSecondOfDay(84399)` | 23:59:59, obtiene tiempo del valor del segundo día|
|`LocalTime.ofNanoOfDay(2000000000)`|00:00:02 , Obtiene tiempo del valor de los nanos del día|