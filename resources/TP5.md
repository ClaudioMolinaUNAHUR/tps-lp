## Parámetros

Los **parámetros** son elementos fundamentales en los lenguajes de programación para **abstraer entradas** a funciones o procedimientos.

Son **nombres formales** que representan los datos que se pasan a una función o procedimiento cuando es invocado.

### Tipos de parámetros

- **Formales:** Los definidos en la declaración de la función.
- **Actuales (argumentos):** Los valores que se pasan cuando se invoca la función.

### Asociaciones comunes
• Asociación por posición
    - **Asociación por posición:** Se enlazan en orden.

    ``saludar("Ana", "Hola")``

• Asociación por nombre
    - **Asociación por nombre:** Se enlazan usando identificadores explícitos.

    ``saludar(mensaje="Buen día", nombre="Ana")``

## Sintaxis

```
<function> := <name-function> "(" <params> ")" <rest-exp>

<params> := λ| <param> | <param> "," <params>

<param> := <name> "=" <valor> | <valor>

<rest-exp> := pueden ser {} o : depende del LP
```
### Notas importantes

- En lenguajes con **tipado estático**, los parámetros deben declararse con su tipo.
- En lenguajes con **tipado dinámico**, los parámetros pueden recibir cualquier tipo de dato.
- En lenguajes **funcionales**, los parámetros pueden no evaluarse hasta que se necesitan (**evaluación perezosa**).

## Tabla de Binding

| **Binding**                                     | **¿Qué es?**                                                                           | **Estático**                                           | **Dinámico**                                    | **Ejemplo estático**                                                                                          | **Ejemplo dinámico**                                                                                             |
| ----------------------------------------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **De valor**                                    | Valor pasado al parámetro al momento de llamar a la función (copiado o referenciado)   | C, Java (primitivos), Kotlin                           | Python, JavaScript, Ruby, Lua                   | ```java:= int x = 10; void sumar(int n) { n += 5; } sumar(x); System.out.println(x);  // 10```               | ```js function sumar(n) { n += 5; } let x = 10; sumar(x); console.log(x);  // 10```                           |
| **De tipo**                                     | Tipo de dato permitido por el parámetro                                                | Java, C++, Kotlin (tipado fuerte y estático)           | Python, JavaScript, PHP (tipado débil/dinámico) | ```java:= void mostrarEdad(int edad) {   System.out.println(edad); }```                                      | ```python:= def mostrarEdad(edad):     print(edad) mostrarEdad("25")  # No lanza error```                       |
| **De nombre**                                   | Nombre del identificador dentro del cuerpo de la función                               | Todos los lenguajes con funciones nombradas            | No aplica                                       | ```java:= int cuadrado(int n) { return n * n; }```                                                              | ```python def cuadrado(n):     return n * n cuadrado(5)```                                                    |
| **De posición o asociación**                    | Forma de enlazar los argumentos a los parámetros formales (por posición, nombre, etc.) | C, Java, Pascal (por posición)                         | Python, Ruby, Lua (soporta posición y nombre)   | ```java:= void saludar(String nombre, int edad) {   System.out.println(nombre + ", " + edad); }```            | ```python:= def saludar(nombre, edad):     print(f"{nombre}, {edad}") saludar(edad=30, nombre="Ana")```         |
| **De dirección o referencia**                   | Si se pasa por referencia (modificable) o por valor (copiado)                          | C++ (`&`), Fortran (`INOUT`), Rust (`&mut`)            | Python (objetos mutables), JavaScript (objetos) | ```cpp:= void aumentar(int& n) { n++; } int x = 5; aumentar(x); // x ahora es 6```                             | ```python:= def aumentar(lista):     lista.append(99) nums = [1, 2] aumentar(nums) print(nums)  # [1, 2, 99]``` |
| **De tiempo de evaluación (binding del valor)** | Cuándo se evalúa el valor del argumento                                                | Lenguajes eager (evaluación estricta): C, Java, Python | Lazy (evaluación diferida): Haskell             | ```java:= int calcular(int x) { return x * 2; } int res = calcular(1 + 2);  // 1+2 se evalúa antes```           | ```haskell:= f x = 42 main = print (f (undefined))  -- OK, nunca se evalúa undefined```                          |
