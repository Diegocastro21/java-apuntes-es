# Uso De Un Setter O Getter Para Implementar Una Restricción

Los **Setter** y **Getter** permiten que un objeto contenga variables privadas
a las que se puede acceder y modificar con restricciones. 

```java
public class Persona {
    
    private String nombre;
    
    public String getNombre(){
        return this.nombre;
    }
    
    public void setNombre(String nombre){
        if (nombre != null && nombre.length()>2) {
            this.nombre = nombre;
        }
    }
    
}
```

En esta Clase `Persona`, tiene una sola variable: `nombre`. Esta variable puede ser accedida usando el metodo `getNombre()`
y cambiarla mediante el metodo `setNombre(String)`, Sin embargo, para establecer un nombre es necesario
que el nuevo nombre tenga una longitud superior a 2 caracteres y que no sea `null`.El uso de un método setter en
lugar de hacer pública la variable nombre permite a otros establecer el valor de nombre con ciertas restricciones.

Lo mismo puede aplicarse al método getter:

```java
public String getNombre(){
    if (nombre.length()>16) 
        return "El Nombre es muy largo!";
    else
        return this.nombre;
}
```

En el método `getNombre()` modificado anteriormente, El nombre es retornado únicamente si la longitud es menor o igual a 16.
De lo contrario retorna, `"El Nombre es muy largo!"`. Esto permite al programador crear variables que son
accesibles y modificables como quiera, evitando que las clases cliente editen las variables de forma no deseada