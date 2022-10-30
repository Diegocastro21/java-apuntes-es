# Agregar Getter Y Setter

La encapsulación es un concepto básico en OOP. Se trata de envolver datos y código como una sola unidad.
En este caso, es una buena práctica declarar las variables como privadas y
luego acceder a ellas a través de Getters y Setters para verlas y/o modificarlas.

```java
public class Ejemplo {
    
    private String nombre;
    private int edad;

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public int getEdad() {
        return edad;
    }

    public void setEdad(int edad) {
        this.edad = edad;
    }
}

```
No se puede acceder a estas variables privadas directamente desde fuera de la clase.
Por lo tanto, están protegidos contra el acceso no autorizado.
Pero si quieres verlos o modificarlos, puedes usar Getters y Setters.

El método getXxx() retornará el valor actual de la variable xxx,
mientras que puede establecer el valor de la variable xxx usando setXxx().

La convención de nomenclatura de los métodos es (en el ejemplo, la variable se llama variableNombre):

* Todas las variables no `boolean`
```java
getVariableNombre()     //Getter, el nombre de la variable empieza con Mayúscula.
setVariableNombre(...) // Setter, El nombre de la variable empieza con Mayúscula.
```
* Variables `boolean`
```java
isVariableNombre()      //Getter, el nombre de la variable empieza con Mayúscula.
setVariableNombre(...) // Setter, El nombre de la variable empieza con Mayúscula.
```

Los getter y setter públicos forman parte de la definición de la propiedad de un Java Bean.