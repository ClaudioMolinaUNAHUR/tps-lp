# Brainfuck
Es un lenguaje de programación esoterico, el cual puede resolver cualquier problema computacional, ya que, se lo considera Turing completo:

# Como programar en Brainfuck?
brainfuck utiliza una cinta de salida con posiciones, donde en cada posición, se va a escribir un número entero. Este número al finalizar va a traducirce a su referido en ASCII
Ejemplo:

| 72 | 79 | 76 | 65 |
| -- | -- | -- | -- |
| H | O | L | A |

la forma en que va a acumular numeros es usando sumas un bucles para lograrlo, utilizando los movimientos para acumular y luego obtener un resultado, tal y como se hace en una Maquina de turing

Su alfabeto consta solo de 9 simbolos

ΣT = { `<` , `>` , `+` , `-` , `.` , `,` , `[` , `]` }

    + = aumentar acumulador
    - = aumentar acumulador
    . = imprimir celda
    < = retroceder en cinta
    > = avanzar en cinta
    , = introducir valor manualmente
    [ = inicio de bucle, si el valor de la celda donde se acumula es 0 sale del loop
    ] = fin del bucle, si volve al inicio de bucle cuando llega a este punto

# Representaciones formales del lenguaje:

Representación BNF:

    <program> ::= <reserved><program> | <reserved>  | λ
    <reserved> ::= <caracter> | <loop>
    <loop> ::= <bracket_open> <program> <bracket_close>
    <caracter> ::= < | > | + | - | . | ,
    <bracket_open> ::= [
    <bracket_close> ::= ]


Representación RegExp:

    RegExp = ( [(< | > | + | - | . | , )*] | (< | > | + | - | . | , ) )*

Representación GIC:

    GIC = <
    ΣT = {`<` , `>` , `+` , `-` , `.` , `,` , `[` , `]`}, 
    ΣN = {S, R, L}, 
    S = S, 
    P = P
    >

```
# Producciones:
S -> RS | R | λ
R -> < | > | + | - | . | , | L
L -> [S]
```

Representacion Extended-BNF (EBNF):

    <program> ::= {<reserved>}*
    <reserved> ::= < | > | + | - | . | , | <loop>
    <loop> ::= [ <program> ]

Representacion Augmented-BNF (ABNF):

    program : { reserved _ op }
    reserved : uno de <  >  +  -  .  ,  loop
    loop : [ program ]


- Compilador Online [Aquí](https://ashupk.github.io/Brainfuck/brainfuck-visualizer-master/index.html#PisrWzwrKys+LV08Lj4rK1s+Kys8LV0+Lj4sCg==)
