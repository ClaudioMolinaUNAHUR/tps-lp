## Beta

# Tipos
Solo acepta letras de a-z A-Z
Solo acepta valores enteros
```
str | num | bool
```
# declaracion e inicialización de variable:
Cuando se declara una variable se la debe inicializar

```
  <tipo> <identificador>: <exp>

  Ejemplo:
  str name: "Jhony"
```

# asignacion:
solo se pueden asignar en las variables aquellos expresiones que retornan alguno de los 3 tipos

```
  <identificador>: <exp>

  Ejemplo:
  name: "Jhony"

  Ejemplo No
  name: funcionSinReturn()
```

# Operadores:

maneja operadores logicos, aritmeticos y de comparacion. Y ademas todos los tipos de datos manejan todos los operadores

```
oper_aritmeticos = + | - | * | /
~El | es el or lógico y el & es el and lógico~
oper_logicos = "&" | "|"    
oper_logicos_unario = !
oper_comparacion = < | > | <= | >= | == | !=

Ejemplo:
"abc" / true
```

# expresiones:
Algunos ejemplos de expresiones:
```
1
0 + 20
true & false
true | false
```

# loop iterador:

los for son solo con numeros, tiene internamente el software una funcion range(`<int>`, `<int>`) que segun el numero que se ponga incrementa o decrementa un numero 0, 1 inc hasta 1, pero si es de 2, 0 dec hasta 0
En caso de que range reciba 1 solo parametro, va de 0 a ese numero - 1
```
loop (<identificador> in range(<int>, <int>)) {<content>}

Ejemplos:
~El identificador "i" va a incrementar de 0 a 2~
loop( i in range(0, 2)) {
  console(i)
}

~El identificador "i" va a decrementar de 2 a 0~
loop( i in range(2, 0)) {
  console(i)
}
```

# conditional:

el condicional lleva dentro una expr que siempre retorna uno de los 3 valores o es simplemente un valor de algun tipo

```
if (<expr>) {<content>}

~La expresion es comparada y luego se ejecuta el contenido~
if("clau" == name) {
  ~En este caso funcionA() deberia se una funcion con return~
  return funcionA()
}

```

# funciones:

El valor por defecto de un parametro se asigna pero es opcional

Los parametros tambien son opcionales

```
func <identificador> (<tipo> param1: <str | num | bool>, ...,<tipo> paramN) {
  <content_func>
}

Ejemplo:
func funcionA (str name: "clau", boolean value) {
  console("Nombre: ", name, "de valor:", value)
}
```

las funciones con return requieren declara el tipo de devolucion

```
func <identificador> (<tipo> param1, ...,<tipo> paramN): <tipo> {
  <content_func>
  return <exp>
}

Ejemplo:
func funcionA (str name: "clau", boolean value): number {
  console("Nombre: ", name, "de valor:", value)
  return 1
}
```

# funciones internas del lenguaje:

range: es una funcion que solo es utilizable en los "loop"s
tiene 1 o 2 parametros
```
range(<num>, <num>)

Ejemplo:
range(1, 2) # 1; 2

range(3) # 0; 1; 2
```

console: es una funcion que imprime en consola el contenido de los argumentos pasados que tienen return
```
console(<args>)

Ejemplo:
console("Nombre: ", name, "de valor:", value)
```
# Iniciar programa:
El program se ejecuta entre estas palabras reservadas, y admite que el contenido sea vacio
```
#start <content> #end
```

# Ejemplos

```
#start
#end
```

```
#start
false
#end
```

```
#start
num x: 10
num result: 0
func sum (num a, num b: 5): num {
    num result: 0
    loop (i in range(0, 10)){
        if(i == a){
            result: a + b
        }
    }
    return result
}
result: sum(x)
console(result) # imprime por consola 15
#end
```

# Caracteristicas:

## General

|                           | **Descripción**                                                            |
|----------------------------------------|----------------------------------------------------------------------------|
| Paradigma                              | Imperativo, estructurado                                                   |
| Tipos de datos                         | Primitivos: `str`, `number`, `boolean`                                     |
| Dominio                                | Especifico                                                                 |
| Tipado                                 | Estático, fuerte                                                           |
| Tipo de Traductor                      | Compilado                                                                  |
| Generación                             | 3 incluye los lenguajes de alto nivel                                      |
| Interactividad                         | No orientado a eventos                                                     |
| Realización visual                     | Textual                                                                    |
| Prediccion del siguiente estado        | Determinista                                                               |
| Inferencia de tipos                    | No     (siempre se debe especificar)                                       |
| Nivel de abstracción                   | Medio    (es estructurado, pero no maneja coleccion ni objetos)            |
| Independencia de la máquina            | Sí    (se ejecuta en cualquier sistema)                                    |
| Orientación a objetos                  | No                                                                         |
| Sensible a mayúsculas                  | Sí                                                                         |
| Esotérico                              | Moderado (solo permite algunos caracteres y operaciones raras "abc" / true)|
| Concurrencia                           | No                                                                         |
| Funcionalidad de retorno               | Opcional (`retorno` en funciones)                                          |
| Casting                                | Implicito  ( siempre resuelve el tipo, no da errores )                     |

## Control de flujo
|                           | **Descripción**                                                            |
|----------------------------------------|----------------------------------------------------------------------------|
| Secuencial                             | Sí ( se ejecuta en orden)                                                  |
| Recursividad                           | Sí (permitida sintácticamente)                                             |
| Pasaje de parámetros                   | Por valor                                                                  |
| Valores por defecto                    | Sí (`tipo param: valor`)                                                   |
| Funciones                              | Sí, con y sin retorno                                                      |
| Modelo de ejecución                    | Interpretado (modelo pseudocódigo)                                         |
| Entrada de datos                       | No                                                                         |
| Manejo de errores                      | No                                                                         |
| Gestión de memoria                     | No modelado                                                                |


# BNF

```bnf
<prog>::= #start <content> #end
<content>::= <content_no_return> | <content_return> | <content_no_return> <content> | <content_return> <content> | λ
<content_no_return>::= <function> |  <loop> | <conditional> | <var> | <assign>
<content_return>::= <function_return> | <console>  | <exp> | <call_func> | <primitive> | <id>
<console>::= console(<args>)
 
<function>::= func <id> (<param>) { <content> }
<function_return>::= func <id> (<param>) : <type> { <content> return <content_return> }
<param>::= <type> <id>,  <param> | <var>, <param> | <type> <id> | <var>

<call_func>::= <id>(<args>) | <id>()

<conditional>::= if ( <content_return> ) { <content> } | if ( <content_return> ) { <content> } else { <content> } | if ( <content_return> ) { <content> } else <conditional>

<loop>::= loop ( <id> in <range>) { <content> }
<range>:: = range(<number>, <number>) | range(<number>)

<exp>::= 
    <content_return> <operator> <content_return> | 
    <content_return> <operator> <exp> | 
    <content_return> | 
    <op_bool_un> <content_return> <operator> <content_return> | 
    <op_bool_un> <content_return> <operator> <exp> | 
    <op_bool_un> <content_return>

<var>::= <type> <id>: <content_return>
<assign>::= <id>: <content_return>
<args>::= <content_return>,<args> | <content_return>
<id>::= <letter> <id> | <letter>

<string>::= "<str_content>" | '<str_content>'
<str_content>::= <letter> <str_content> | <str_content>

<primitive> ::= <number> | <boolean> | <string>
<operator> ::= <op_arit> | <op_bool_bin> | <op_comp>
<number> ::= <int> <number> | <number>
<type> ::= str | number | boolean
<op_arit> ::= + | - | * | / | %
<op_bool_bin>::= & | `|`
<op_bool_un>::= !
<op_comp>::= < | > | <= | >= | == | !=
<boolean>::= true | false
<letter>::= a | b | c | d | e | f | g | h | i | j | k | l | m | n | o | p | q | r | s | t | u | v | w | x | y | z | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | Z
<int>::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
```
