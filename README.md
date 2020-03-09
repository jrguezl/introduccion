## Temas

<ul>
{% for tema in site.temas %}
  <li><a href="{{site.baseurl}}{{tema.url}}" title="{{ tema.hover }}">{{ tema.title }}</a></li>
{% endfor %}
</ul>


## Clases 

{% include clases-impartidas.md %}

## Prácticas

{% include practicas-publicadas.md  %}

<!--
## [El Grado](degree.md)

## [Recursos](resources.md)

## [Exámenes de convocatoria](exams.md)

## [Calendarios, Horarios y Exámenes](timetables.md)

## [Referencias](references.md)

## [Tema 0: La Asignatura de PL. Guía Docente](tema0-introduccion-a-pl/guia-docente.md)

### [Práctica pb-gh-campus-expert](tema0-introduccion-a-pl/practicas/pb-gh-campus-expert)

### [Práctica p0-t0-esprima-logging](tema0-introduccion-a-pl/practicas/p0-t0-esprima-logging)

## [Tema 1: Introducción a JavaScript](tema1-introduccion-a-javascript/)

### [Práctica de Manejo del iaas.ull.es (p1-t1-iaas)](tema1-introduccion-a-javascript/practicas/p1-t1-iaas/README.md)

### [Práctica de Testing. Traduciendo de XML a JSON (p2-t1-testing)](tema1-introduccion-a-javascript/practicas/p2-t1-testing/)

## [Tema 2: Expresiones Regulares y Análisis Léxico](tema2-expresiones-regulares-y-analisis-lexico/README.md)

### [ Práctica de Expresiones Regulares (p3-t2-regexp)](tema2-expresiones-regulares-y-analisis-lexico/practicas/p3-t2-regexp/reto)

### [Práctica Escribir un Analizador Léxico para Javascript (p4-t2-lexer)](tema2-expresiones-regulares-y-analisis-lexico/practicas/p4-t2-lexer/README.md)

## [Tema 3: Análisis Sintáctico Descendente Recursivo (e Interpretación de Código)](tema3-analisis-descendente-predictivo-recursivo)

### [Práctica p5-t3-egg-0](tema3-analisis-descendente-predictivo-recursivo/practicas/p5-t3-egg-0)

### [Práctica p6-t3-egg-1](tema3-analisis-descendente-predictivo-recursivo/practicas/p6-t3-egg-1)

### [Práctica p7-t3-egg-1](tema3-analisis-descendente-predictivo-recursivo/practicas/p6-t3-egg-1)

### [Práctica p8-t3-pdr-infix2egg](tema3-analisis-descendente-predictivo-recursivo/practicas/p8-t3-pdr-infix2egg)

## [Tema 4: Parsing Expression Grammars](tema4-parsing-expression-grammars)

### [Práctica p9-t4-peg-infix2egg](tema4-parsing-expression-grammars/practicas/p9-t4-peg-infix2egg)

## [Tema 5: Análisis Ascendente](tema5-analisis-ascendente)

### [Práctica p10-t5-jison-infix2egg](tema5-analisis-ascendente/practicas/p10-t5-jison-infix2egg)


## [Tema 6: Análisis Dependiente del Contexto](tema6-analisis-dependiente-del-contexto)
-->