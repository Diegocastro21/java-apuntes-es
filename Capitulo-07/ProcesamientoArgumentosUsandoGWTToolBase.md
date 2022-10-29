#  Procesamiento de argumentos utilizando GWT ToolBase
Si desea analizar argumentos de línea de comandos más complejos, por ejemplo, con parámetros opcionales, lo mejor es usar el enfoque GWT de Google. Todas las clases están disponibles en público en:

[Enfoque GWT de Google](https://gwt.googlesource.com/gwt/+/2.8.0-beta1/dev/core/src/com/google/gwt/util/tools/ToolBase.java)

Un ejemplo para manejar la línea de comandos `miprograma` -dir **"~/Documents"** -port **8888** es:

```java
public class MyProgramHandler extends ToolBase { 
    protected File dir;
    protected int port;
    // getters for dir and port
    ...
    
    public MyProgramHandler() { 
        this.registerHandler(new ArgHandlerDir() {
            @Override
            public void setDir(File dir) {
                this.dir = dir; 
            }
        });
        this.registerHandler(new ArgHandlerInt() {
            @Override
            public String[] getTagArgs() {
            return new String[]{"port"}; 
            }
            @Override
            public void setInt(int value) {
                this.port = value; }
        
        }); 
    }
    public static void main(String[] args) { 
        MyProgramHandler myShell = new MyProgramHandler(); 
        if (myShell.processArgs(args)) {
             // main program operation
             System.out.println(String.format("port: %d; dir: %s",
                myShell.getPort(), myShell.getDir()));
        }
        System.exit(1);
   }
}
```
`ArgHandler` también tiene un método `isRequired()` que se puede sobrescribir para decir que el argumento de la línea de comandos es obligatorio
la devolución predeterminada es **false** para que el argumento sea opcional.

