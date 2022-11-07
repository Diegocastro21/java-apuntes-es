# El Primitivo char
Un carácter puede almacenar un solo `char` Unicode de 16 bits.
Un carácter literal está encerrado en comillas únicas
```java
char myChar = 'u';
char myChar2 = '5';
char myChar3 = 65; // myChar3 == 'A'
```
Tiene un valor mínimo de `\u0000` (0 en la representación decimal, también llamado carácter nulo) 
y un valor máximo de `\uffff` (65.535).

El valor predeterminado de un `char` es `\u0000`.
```java
char defaultChar;   // default == \u0000
```
Para definir un carácter de `'` valor, se debe utilizar una secuencia de escape (cacter precedido por una barra invertida):
```java
char singleQuote = '\';
```
También hay otras secuencias de escape:
```java
char tab = '\t';
char backspace = '\b';
char newline = '\n';
char carriageReturn = '\r';
char formfeed = '\f';
char singleQuote = '\'';
char doubleQuote = '\"'; // Escapar redundante aquí; '"' sería lo mismo; sin embargo, todavía está permitido
char backslash = '\\';
char unicodeChar = '\uXXXX' // XXXX representa el valor Unicode del carácter que desea mostrar
```
Puedes declarar un carácter de cualquier `char` Unicode.
```java
char heart = '\u2764';
System.out.println(Character.toString(heart)); // imprime una linea que contiene --> "❤".
```
También es posible añadir a un `char`. 
Por ejemplo, para iterar a través de cada letra minúscula, podría hacer lo siguiente:
```java
for (int i = 0; i <= 25; i++) {
    char letter = (char) ('a' + i);
    System.out.println(letter);
}
```
salida:
```java
a
b
c
d
e
f
g
h
i
j
k
l
m
n
o
p
q
r
s
t
u
v
w
x
y
z
```