# Consumo de memoria de primitivas frente a boxed primitivas
| Primitiva | Tipo Boxed | Tamaño de la memoria de primitivo / boxed |
|-----------|------------|-------------------------------------------|
| boolean   | Boolean    | 1 byte / 16 bytes                         |
| byte      | Byte       | 1 byte / 16 bytes                         |
| short     | Short      | 2 bytes / 16 bytes                        |
| char      | Char       | 2 bytes / 16 bytes                        |
| int       | Integer    | 4 bytes / 16 bytes                        |
| long      | Long       | 8 bytes / 16 bytes                        |
| float     | Float      | 4 bytes / 16 bytes                        |
| double    | Double     | 8 bytes / 16 bytes                        |
Los objetos en caja siempre requieren 8 bytes para la gestión de tipos y memoria, y debido a que el tamaño de los objetos siempre es un múltiplo de 8,
todos los tipos en caja requieren un total de 16 bytes. Además, cada uso de un objeto en boxed implica almacenar una referencia que representa otros 4 u 8 bytes,
dependiendo de las opciones JVM y JVM.

En las operaciones intensivas de datos,
el consumo de memoria puede tener un gran impacto en el rendimiento. 
El consumo de memoria crece aún más cuando se utilizan matrices: una matriz `float[5]` requerirá solo 32 bytes;
mientras que un `Float[5]` que almacene 5 valores distintos no nulos requerirá 112 bytes en total
(en 64 bits sin punteros comprimidos, esto aumenta a 152 bytes).

### Cachés de valor en boxed

Los gastos generales de espacio de los tipos en caja se pueden mitigar hasta cierto punto con las cachés de valores en caja.
Algunos de los tipos en caja implementan una caché de instancias. Por ejemplo, de forma predeterminada,
la clase `Integer` almacenará en caché las instancias para representar números en el rango de `-128` a `+127`.
Sin embargo, esto no reduce el costo adicional derivado de la indirección de la memoria adicional.

Si crea una instancia de un tipo en caja, ya sea mediante autoboxing
o llamando al método static `valueOf(primitive)`, 
el sistema de tiempo de ejecución intentará utilizar un valor en caché.
Si su aplicación utiliza muchos valores en el rango que se almacena en caché,
esto puede reducir sustancialmente la penalización de memoria del uso de tipos en boxed.
Ciertamente, si está creando instancias de valor en boxed "a mano", es mejor usar `valueOf` en lugar de `new`. 
(La `new` operación siempre crea una nueva instancia).
Sin embargo, si la mayoría de sus valores no están en el rango en caché,
puede ser más rápido llamar a `new` y guardar la búsqueda de caché.