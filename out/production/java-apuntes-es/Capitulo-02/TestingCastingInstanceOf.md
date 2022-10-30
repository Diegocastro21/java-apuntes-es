# Comprobación Si Un Objeto Puede Ser Casteado Usando instanceof 

Java proporciona el operador `instanceof` para testear si un objeto es de un tipo determinado,
una subclase de ese tipo. El programa puede entonces elegir entre castear o no castear ese objeto en consecuencia.

```java
Object obj = Calendar.getInstance();
long time = 0;

if (obj instanceof Calendar){
    time = ((Calendar)obj).getTime();
}

if (obj instanceof Date) {
    time = ((Date)obj).getTime();  // Esta línea nunca será alcanzada, obj no es un tipo Date
}
```