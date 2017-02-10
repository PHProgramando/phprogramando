
Capítulo 3
==========

Nesse capítulo aprendemos sobre as estruturas de controle. Como o nome
sugere elas servem para controlar como seu código vai funcionar, são as
famosas tomadas de decisão. Faremos também uso dos operadores visto no
Capítulo 2.

Estrutura de controle
---------------------

O PHP divide a estrutura de controle em duas partes. As condicionais que
fazem testes no seu código como o *if* e *switch*, e as repetições que
fazem iterações no seu código como o *while*, *do*, *for* e *foreach*.

### Condicionais

Crie um diretório chamado */home/seu\_usuario/www/Cap3/*.

#### If

1.  ...

2.  &lt;h1&gt;If&lt;/h1&gt;

3.  &lt;?php

4.  \$idade = 18;

5.  6.  //Testa se usuário tem 18 anos ou mais

7.  if (\$idade &gt;= 18) {

8.  echo 'Opa, já posso dirigir e beber';

9.  }

10. ?&gt;

11. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional1.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional1.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional1.php)[*/*](http://localhost/PHPBasico/Cap3/condicional1.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional1.php)[*3*](http://localhost/PHPBasico/Cap3/condicional1.php)[*/*](http://localhost/PHPBasico/Cap3/condicional1.php)[*condicional1*](http://localhost/PHPBasico/Cap3/condicional1.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional1.php).

Nota: Repare que entre o “**if**” e o parênteses “**(**“, existe um
espaço, o mesmo ocorre entre o fechamento do parênteses “**)**” e a
abertura da chaves “**{**“. Não há espaço depois da abertura nem
fechamento das chaves.[^2]

#### else

1.  ...

2.  &lt;h1&gt;If&lt;/h1&gt;

3.  &lt;?php

4.  \$idade = 18;

5.  6.  //Testa se usuário tem 18 anos ou mais

7.  if (\$idade &gt;= 18) {

8.  //retorna true

9.  echo 'Opa, já posso dirigir e beber';

10. } else {

11. //retorna false

12. echo 'Não posso dirigir nem beber';

13. }

14. ?&gt;

15. ?&gt;

16. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional2.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional2.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional2.php)[*/*](http://localhost/PHPBasico/Cap3/condicional2.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional2.php)[*3*](http://localhost/PHPBasico/Cap3/condicional2.php)[*/*](http://localhost/PHPBasico/Cap3/condicional2.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional2.php)[*2*](http://localhost/PHPBasico/Cap3/condicional2.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional2.php).

#### If, elseif e else

1.  ...

2.  &lt;h1&gt;If, Elseif e Else&lt;/h1&gt;

3.  &lt;?php

4.  \$idade = 18;

5.  6.  //Testa se usuário tem 18 anos ou mais

7.  if (\$idade &gt;= 18) {

8.  //retorna true

9.  echo 'Opa, já posso dirigir e beber';

10. } elseif (\$idade &gt;= 12 && \$idade &lt;= 17) {

11. //retorna true se idade for maior e

12. //igual a 17 e menor e igual a 10

13. echo 'Não posso dirigir nem beber';

14. } else {

15. //retorna false

16. echo 'Muito criança, não vai nem para escola sozinho';

17. }

18. ?&gt;

19. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional3.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional3.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional3.php)[*/*](http://localhost/PHPBasico/Cap3/condicional3.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional3.php)[*3*](http://localhost/PHPBasico/Cap3/condicional3.php)[*/*](http://localhost/PHPBasico/Cap3/condicional3.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional3.php)[*3*](http://localhost/PHPBasico/Cap3/condicional3.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional3.php).

#### Outro exemplo if e eles

1.  ...

2.  &lt;h1&gt;If e Else&lt;/h1&gt;

3.  &lt;?php

4.  \$cpf = '00000000000001';

5.  6.  if (\$cpf == "00000000000000" ||

7.  \$cpf == "11111111111111" ||

8.  \$cpf == "22222222222222" ||

9.  \$cpf == "33333333333333" ||

10. \$cpf == "44444444444444" ||

11. \$cpf == "55555555555555" ||

12. \$cpf == "66666666666666" ||

13. \$cpf == "77777777777777" ||

14. \$cpf == "88888888888888" ||

15. \$cpf == "99999999999999") {

16. echo "CPF inválido!";

17. } else {

18. echo "CPF informado: " . \$cpf;

19. }

20. ?&gt;

21. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional4.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional4.php)[*3*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional4.php)[*4*](http://localhost/PHPBasico/Cap3/condicional4.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional4.php).

Veremos agora outra forma de condicional o switch (\$var) … case.

#### Switch

Assim como no if, esse comando fará comparações, e caso o valor seja
verdadeiro, entrará na condição. Vamos a um exemplo bem simples.

1.  …

2.  &lt;h1&gt;switch e case&lt;/h1&gt;

3.  &lt;?php

4.  \$cor = 'azul';

5.  6.  switch (\$cor) {

7.  case 'azul':

8.  echo 'A variável \$cor é azul';

9.  break;

10. 11. case 'verde':

12. echo 'A variável \\\$cor é verde';

13. break;

14. }

15. ?&gt;

16. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional5.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional4.php)[*3*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional4.php)[*5*](http://localhost/PHPBasico/Cap3/condicional4.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional4.php).

Note que no final de cada case exite o comando break, esse comando é
obrigatório, e será explicado em outro exercício.

1.  ...

2.  &lt;h1&gt;switch e case&lt;/h1&gt;

3.  &lt;?php

4.  \$cor = 'verde1';

5.  6.  switch (\$cor) {

7.  case 'azul':

8.  echo 'A variável \$cor é ' . \$cor;

9.  break;

10. 11. case 'verde':

12. echo 'A variável \$cor é ' . \$cor;

13. break;

14. 15. default:

16. echo 'A variável \$cor é preto';

17. break;

18. }

19. ?&gt;

20. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional6.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional6.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional6.php)[*/*](http://localhost/PHPBasico/Cap3/condicional6.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional6.php)[*3*](http://localhost/PHPBasico/Cap3/condicional6.php)[*/*](http://localhost/PHPBasico/Cap3/condicional6.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional6.php)[*6*](http://localhost/PHPBasico/Cap3/condicional6.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional6.php).

O comando **default**:, serve como um “**else**”, ou seja, no caso de
false em todos os “**case**” ele assume um valor padrão.

1.  ...

2.  &lt;h1&gt;switch e case&lt;/h1&gt;

3.  &lt;?php

4.  \$beer = 'Colarinho';

5.  6.  switch (\$beer) {

7.  case 'Coruja':

8.  case 'ERDINGER':

9.  case 'Colarinho':

10. case 'Paulaner':

11. echo 'Ótimas cervejas!';

12. break;

13. case 'Colorado':

14. case 'Rogue':

15. case 'Perigosa':

16. echo 'Cerveja muito amarga e parece caldo de cana!';

17. break;

18. default:

19. echo 'Prefiro cervejas de trigo!';

20. break;

21. }

22. ?&gt;

23. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional7.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional7.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional7.php)[*/*](http://localhost/PHPBasico/Cap3/condicional7.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional7.php)[*3*](http://localhost/PHPBasico/Cap3/condicional7.php)[*/*](http://localhost/PHPBasico/Cap3/condicional7.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional7.php)[*7*](http://localhost/PHPBasico/Cap3/condicional7.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional7.php).

Nota: Repare que entre o “**switch**” e o parênteses “**(**“, existe um
espaço, o mesmo ocorre entre o fechamento do parênteses “**)**” e a
abertura da chaves “**{**“. Não há espaço depois da abertura nem
fechamento das chaves.[^3]

### Repetição

As estruturas de repetições ou laços, servem para que uma determinada
situação seja repetida enquanto ela seja verdadeira. Fazem parte dessa
lista o while, do, for e foreach.

#### While

1.  ...

2.  &lt;h1&gt;While&lt;/h1&gt;

3.  &lt;?php

4.  \$contador = 1;

5.  6.  while (\$contador &lt;= 10) {

7.  echo \$contador++;

8.  echo '&lt;br /&gt;';

9.  }

10. ?&gt;

11. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao1.php*, no
browser digite <http://localhost/PHPBasico/Cap3/repeticao1.php>.

Nota: Assim como no **if** e no **switch**, observe o espaço entre o
comando “**while**” e o parênteses “**(**“ e o espaço entre o fechamento
do parênteses “**)**” com a abertura da chave “**{**“.[^4]

#### Do while

1.  ...

2.  &lt;h1&gt;Do While&lt;/h1&gt;

3.  &lt;?php

4.  \$contador = 11;

5.  6.  do {

7.  echo \$contador++;

8.  echo '&lt;br /&gt;';

9.  } while (\$contador &lt;= 10);

10. ?&gt;

11. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao2.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao1.php)[2](http://localhost/PHPBasico/Cap3/repeticao1.php)[.php](http://localhost/PHPBasico/Cap3/repeticao1.php).

Nota: A diferença entre o **while** e o **do while** é que o **while**
testa se é verdadeiro e executa enquanto o **do while** executa pelo
menos uma vez antes de testar. Veja a forma como foi codificado o **do
while**, segue o mesmo padrão do FIG[^5]

#### For

1.  ...

2.  &lt;h1&gt;For&lt;/h1&gt;

3.  &lt;?php

4.  for (\$i = 1; \$i &lt;= 10; \$i++) {

5.  echo \$i . '&lt;br /&gt;';

6.  }

7.  ?&gt;

8.  ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao3.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao1.php)[3](http://localhost/PHPBasico/Cap3/repeticao1.php)[.php](http://localhost/PHPBasico/Cap3/repeticao1.php).

#### For com array

1.  ...

2.  &lt;h1&gt;For com array&lt;/h1&gt;

3.  &lt;?php

4.  \$vetor = array(1, 2, 3, 4, 5);

5.  6.  for (\$i = 0; \$i &lt; 5; \$i++) {

7.  \$item = \$vetor\[\$i\];

8.  echo \$item . '&lt;br /&gt;';

9.  }

10. ?&gt;

11. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao4.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao4.php)[4](http://localhost/PHPBasico/Cap3/repeticao4.php)[.php](http://localhost/PHPBasico/Cap3/repeticao4.php).

#### Foreach simples

1.  ...

2.  &lt;h1&gt;Foreach Simples&lt;/h1&gt;

3.  &lt;?php

4.  \$vetor = array(1, 2, 3, 4, 5);

5.  6.  foreach (\$vetor as \$item) {

7.  echo \$item . '&lt;br /&gt;';

8.  }

9.  ?&gt;

10. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao5.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao5.php)[5](http://localhost/PHPBasico/Cap3/repeticao5.php)[.php](http://localhost/PHPBasico/Cap3/repeticao5.php).

#### Foreach chave (key) e valor (value)

1.  ...

2.  &lt;h1&gt;Foreach chave valor&lt;/h1&gt;

3.  &lt;?php

4.  \$motos = \[

5.  1 =&gt; 'Suzuki',

6.  2 =&gt; 'Yamaha',

7.  3 =&gt; 'Honda',

8.  4 =&gt; 'Triumph',

9.  5 =&gt; 'Ducati'

10. \];

11. 12. foreach (\$motos as \$key =&gt; \$value) {

13. echo \$key . ' - ' . \$value . '&lt;br /&gt;';

14. }

15. ?&gt;

16. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao6.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao5.php)[6](http://localhost/PHPBasico/Cap3/repeticao5.php)[.php](http://localhost/PHPBasico/Cap3/repeticao5.php).

Nota: o **for** e o **foreach** também seguem a padronização do FIG[^6]

Resumo do capítulo
------------------

Nesse capítulo aprendemos um pouco mais do básico do PHP. Vimos como é
possível tomar decisões no código com os comandos ***if***, ***else*** e
***elseif***, e com o comando ***switch*** ***case***, uma outra maneira
de tomar decisões. Com os comandos ***while***, ***do while***,
***for*** e ***foreach*** descobrimos como repetir informações de uma
coleção de dados ou lista.

Exercícios
----------

1.  Crie um script que informe se o aluno foi “Aprovado”, “Reprovado” ou
    está em “Recuperação”. Com os seguintes critérios, maior ou igual a
    7, aluno está aprovado, menor ou igual a 5, aluno reprovado.

2.  Crie uma estrutura de controle com o “switch case” para exibir se um
    modelo de carro é do ano atual ou não.

3.  Crie um contador cujo exiba o valor de 4 até 100 contando de 2 em 2,
    ou seja, 4, 6, 8 etc.

4.  Aproveite o arquivo exemplo4.php do Capítulo 1 para listar todos os
    itens e subitens do array “\$compras” criado no arquivo.

5.  Crie um script que conte de 0 até 1000 e quando chegar no número da
    sua idade, escreva na tela “Eu tenho X anos” e quando chegar ao
    número 169 interromper o script.
