# Por Qué Utilizar Getters Y Setters

Considere un clase basica que contiene un objeto con sus getter y setter:

```java
public class ContenedorCuentas {
    private int contador = 0;

    public int getContador() {
        return contador;
    }

    public void setContador(int contador) {
        this.contador = contador;
    }
}
```
No podemos acceder a la variable de `contador` porque es privada. 
Pero podemos acceder a los métodos `getContador()` y `setContador(int)` porque son públicos.
Para algunos, esto podría plantear la pregunta; 
¿por qué presentar al intermediario? 
¿Por qué no simplemente hacer que contador este al público?
```java
public class ContenedorCuentas {
    private int contador = 0;
}
```
A todos los efectos, estos dos son exactamente iguales, en cuanto a funcionalidad.
La diferencia entre ellos es la extensibilidad. Considera lo que dice cada clase:

* Primero: "Tengo un método que te dará un valor `int`, y un método que establecerá ese valor a otro int".
* Segundo: "Tengo un `int` que puedes configurar y obtener como desees".

Estos pueden sonar similares, pero el primero es en realidad mucho más **guardado** en su naturaleza; solo te
permite interactuar con su naturaleza **interna** como dicta. Esto deja la pelota en su cancha; puede elegir cómo se
producen las interacciones internas.
El segundo ha expuesto su implementación interna externamente, 
y ahora no solo es propenso a usuarios externos, sino que, en el caso de una API, se ha **comprometido** a mantener
esa implementación (o lanzar una API no compatible con versiones anteriores).

Consideremos si queremos sincronizar el acceso para modificar y acceder al contador. En el primero, esto es simple:

```java
public class ContenedorCuentas {
    private int contador = 0;

    public synchronized int getContador() {
        return contador;
    }

    public synchronized void setContador(int contador) {
        this.contador = contador;
    }
}
```

Pero en el segundo ejemplo, esto ahora es casi imposible sin pasar y modificar cada lugar donde se hace referencia a la variable de `contador`.
Peor aún, si este es un elemento que está proporcionando en una biblioteca para ser consumido por otros,
**no** tiene una forma de realizar esa modificación y se ve obligado a tomar la difícil decisión mencionada anteriormente.

Así que plantea la pregunta: ¿las variables públicas son alguna vez algo bueno (o, al menos, no malos)?

No estoy seguro. Por un lado, puede ver ejemplos de variables públicas que han resistido la prueba del tiempo
(IE: la variable out a la que se hace referencia en System.out).
Por otro lado, proporcionar una variable pública no da ningún beneficio aparte de los gastos generales
extremadamente mínimos y la posible reducción de la palabra. Mi consejo aquí sería que, si está planeando 
hacer pública una variable, debe juzgarla en contra de estos criterios con un prejuicio **extremo**:

1. La variable no debería tener ninguna razón concebible para cambiar **nunca** en su implementación. Esto es algo que es extremadamente fácil de arruinar (y, incluso si lo haces bien, los requisitos pueden cambiar), por lo que los getters/setters son el enfoque común. Si vas a tener una variable pública, esto realmente necesita ser pensado, especialmente si se publica en una library/Framework/API.

2. Es necesario hacer referencia a la variable con la suficiente frecuencia como para que las ganancias mínimas de la reducción de la verbosidad la justifiquen. 
Ni siquiera creo que los gastos generales por usar un método en comparación con la referencia directa deban considerarse aquí.
Es demasiado insignificante para lo que estimaría conservadoramente el 99,9 % de las solicitudes.

Si alguna vez tienes dudas, **usa siempre getters/setters.**