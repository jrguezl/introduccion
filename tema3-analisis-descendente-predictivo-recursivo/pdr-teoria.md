# Análisis Sintáctico Predictivo Recursivo {#section:predictivo}

La siguiente fase en la construcción del analizador es la fase de
análisis sintáctico. Esta toma como entrada el flujo de terminales y
construye como salida el árbol de análisis sintáctico abstracto.

El árbol de análisis sintáctico abstracto es una representación
compactada del árbol de análisis sintáctico concreto que contiene la
misma información que éste.

Existen diferentes métodos de análisis sintáctico. La mayoría caen en
una de dos categorías: 

1. ascendentes y 
2. descendentes. 
 
Los ascendentes
construyen el árbol desde las hojas hacia la raíz. 

Los descendentes lo
hacen en modo inverso. 

El que describiremos aquí es un descendente: se denomina **método de análisis predictivo descendente recursivo**.

## Introducción {#subsection:introduccion}

En este método se asocia una subrutina con cada variable sintáctica
$$A \in V$$. Dicha subrutina (que llamaremos `parseA()`) reconocerá el lenguaje
generado desde la variable $$A$$:

$$L_A(G) = \{ x \in \Sigma^* : A \stackrel{*}{\Longrightarrow} x \}$$

En este método se escribe una rutina `parseA` por cada variable sintáctica en la gramática $$A \in V$$. 

Se le suele dar a la rutina asociada un nombre relacionado con la
variable sintáctica asociada, por ejemplo `parseA` será la función asociada con
la variable $$A \in V$$.

La función de `parseA()` es reconocer el lenguaje $$L(A)$$ generado por $$A$$.

La estrategia general que sigue la rutina `parseA` para reconocer $$L(A)$$ es
decidir en términos del terminal `a` en la entrada cual de las partes derechas de las reglas de $$A$$

$$A \rightarrow \alpha_1$$ 

$$A \rightarrow \alpha_2$$ 

$$ \ldots $$

$$A \rightarrow \alpha_n$$ 


se aplica para a continuación comprobar que la entrada que sigue pertenece al lenguaje generado por $$\alpha$$. 

En un analizador predictivo descendente recursivo (APDR) se
asume que el símbolo que actualmente esta siendo observado (que a partir de ahora denominaré `lookahead`) permite determinar unívocamente que producción de $$A$$ hay
que aplicar. 

Una vez que dentro del cuerpo de  `parseA` se ha determinado que la regla concreta por la que 
continuar la derivación es la regla $$A \rightarrow \alpha$$, el algoritmo procede a reconocer
$$L_{\alpha}(G)$$, el lenguaje generado por la parte derecha de la regla $$\alpha$$. 

Para ello se procede así. Si $$\alpha = X_1 \ldots X_n$$, 

- las apariciones de terminales $$X_i$$ en
$$\alpha$$ son emparejadas con los terminales en la entrada avanzando en el flujo de tokens, mientras que
- las apariciones de variables sintácticas $$X_i = B \in V$$ en $$\alpha$$ se traducen en
llamadas a la correspondiente subrutina asociada con `parseB`.


La secuencia de llamadas cuando se procesa la entrada mediante el
siguiente programa construye "implícitamente" el árbol de análisis
sintáctico concreto.

El análisis predictivo confía en que, si
estamos ejecutando la entrada del procedimiento `parseA`, el cuál está
asociado con la variable $$A \in V$$, el símbolo terminal que esta en la
entrada $$a$$ determine de manera unívoca cual de las regla de producción
$$A \rightarrow a \alpha$$ debe ser procesada.

Si se piensa, esta condición requiere que todas las partes derechas
$$\alpha$$ de las reglas $$A \rightarrow \alpha$$ de $$A$$ "comiencen" por
diferentes símbolos. Si denotamos por  $$FIRST(\alpha)$$ al conjunto de terminales que aparecen en una derivación desde $$\alpha$$ al principio:

$$FIRST(\alpha) = \left \{ b \in \Sigma :  \alpha  \stackrel{*}{\Longrightarrow}  b \beta \right \}$$

Podemos reformular ahora nuestra afirmación anterior en estos términos:
Si $$A \rightarrow \gamma_1 \mid \ldots \mid \gamma_n$$ y los conjuntos
$$FIRST(\gamma_i)$$ son disjuntos podemos construir el procedimiento para
la variable $$A$$ siguiendo este seudocódigo:

    function parseA() {
      if (lookahead in FIRST(gamma_1)) { imitar gamma_1 }
      else if (lookahead in FIRST(gamma_2)) { imitar gamma_2 }
      ...
      else (lookahead in FIRST(gamma_n)) { imitar gamma_n }
    }

Donde si $$\gamma_j$$ es $$X_1 \ldots X_k$$ el código `gamma_j` consiste en
una secuencia $$i = 1 \ldots k$$ de llamadas de uno de estos dos tipos:

-   Llamar a la subrutina `parseX_i()` si $$X_i$$ es una variable sintáctica

-   Hacer una llamada al analizador léxico  avanzando sobre el token `lexer()` si $$X_i$$ es el terminal actual
