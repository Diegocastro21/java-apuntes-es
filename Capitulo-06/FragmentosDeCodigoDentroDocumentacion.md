# Fragmentos De Código Dentro De La Documentación

La forma canónica de escribir código dentro de la documentación es con la construcción {@code }. Si tienes un código 
de varias líneas dentro de **`<pre></pre>`**.

```java
/**
 * The Class TestUtils.
 * <p>
 * This is an {@code inline("code example")}.
 * <p>
 * You should wrap it in pre tags when writing multiline code.
 * <pre>{@code
 *  Example example1 = new FirstLineExample();
 *  example1.butYouCanHaveMoreThanOneLine();
 * }</pre>
 * <p>
 * Thanks for reading.
 */
class TestUtils {
```
A veces es posible que tengas que poner algún código complejo dentro del comentario de javadoc.
El signo @ es especialmente problemático. El uso de la antigua etiqueta `<code> `
junto con la construcción {@literal } resuelve el problema.

```java
/**
 * Usage:
 * <pre><code>
 * class SomethingTest {
 * {@literal @}Rule
 *  public SingleTestRule singleTestRule = new SingleTestRule("test1");
 *
 * {@literal @}Test
 * public void test1() {
 * // only this test will be executed *}
 *
 * ...
 *}
 * </code></pre>
 */
class SingleTestRule implements TestRule { }
```
