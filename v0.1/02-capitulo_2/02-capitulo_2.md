
Capítulo 2
==========

Nesse capítulo aprenderemos sobre os operadores suportados pelo PHP.
Quais seus tipos precedências e seus tipos.

Operadores
----------

Um operador é utilizado para realizar operações entre um ou mais valores
(ou expressões, no jargão de programação) e retornar apenas um valor
final. Vamos agora aos operadores.

### Aritméticos

Só podem ser utilizados quando os operandos são números (integer ou
float). Se forem de outro tipo, terão seus valores convertidos antes da
realização da operação.

  - \+    Adição
  - \-    Subtração
  - \*   Multiplicação
  - \/    Divisão
  - \%    Módulo (resto da divisão)

### De strings

Só há um operador exclusivo para strings (ponto):

  - \.   Concatenação

### De atribuição

Existe um operador básico de atribuição e diversos derivados. Sempre
retornam o valor atribuído. No caso dos operadores derivados de
atribuição, a operação é feita entre os dois operandos, sendo atribuído
o resultado para o primeiro. A atribuição é sempre por valor, e não por
referência.

  - \=     Atribuição simples
  - \+=    Atribuição com adição
  - \-=    Atribuição com subtração
  - \*=   Atribuição com multiplicação
  - \/=    Atribuição com divisão
  - \%=    Atribuição com módulo
  - \.=    Atribuição com concatenação

### 

### Bit a bit

Comparam dois números bit a bit.

  - \&          “e” lógico
  - \|          “ou” lógico (pipe)
  - \^         “ou” exclusivo
  - \~         Não (inversão)
  - &lt;&lt;   shift left
  - &gt;&gt;   shift right

### Lógico

Utilizados para inteiros representando valores booleanos.

  - and   “e” lógico
  - or    “ou” lógico (pipe)
  - xor   “ou” exclusivo
  - !     Não (inversão)
  - &&    “e” lógico
  - ||    “ou” lógico (pipe pipe)

### Comparação

As comparações são feitas entre os valores contidos nas variáveis, e não
as referências. Sempre retornam um valor booleano.

  - ==      Igual a
  - !       Diferente
  - &lt;    Menor que
  - &gt;    Maior que
  - &lt;=   Menor ou igual a
  - &gt;=   Maior ou igual a

### Expressão condicional ou ternária

Existe um operador de seleção que é ternário. O interpretador PHP avalia
a primeira expressão. Se ela for verdadeira, a expressão retorna o valor
de expressão2. Senão, retorna o valor de expressão3.

`<?php ( expressao1 ) ? ( expressao2 ) : ( expressao3 );`

### 

### De incremento ou Decremento

Podem ser utilizados de duas formas: antes ou depois da variável. Quando
utilizado antes, retorna o valor da variável antes de incrementá-la ou
decrementá-la. Quando utilizado depois, retorna o valor da variável já
incrementado ou decrementado.

  - \++   Incremento
  - \--   Decremento

### Ordem de precedências dos operadores

  Precedência   Associatividade   Operadores
  -------------
  -             Esquerda          ,
  -             Esquerda          or
  -             Esquerda          xor
  -             Esquerda          and
  -             Direita           print
  -             Esquerda          \=, \+=, \-=, \*=, /=, \.=, \%=, \&=, \!=, \~=, &lt;&lt;= e &gt;&gt;=
  -             Esquerda          ? e :
  -             Esquerda          \||
  -             Esquerda          \&&
  -            Esquerda          \|
  -            Esquerda          \&
  -            Esquerda          \^
  -            Não associa       \== e \!=
  -            Não associa       &lt;, &lt;=, &gt; e &gt;=
  -            Esquerda          &lt;&lt; e &gt;&gt;
  -            Esquerda          \+, \- e \.
  -            Esquerda          \*, \/ e \%
  -            Direita           \!, \~, \++, \--, (int), (double), (string), (array), (object) e \@
  -            Direita           \@
  -            Não associa       new

Resumo do Capítulo
------------------

Nesse capítulo aprendemos sobre os operadores lógicos e matemáticos que
o PHP trabalha. Eles são muito importante pois usará eles praticamente
em todo seu site ou, pelo menos, uma vez em cada script.
