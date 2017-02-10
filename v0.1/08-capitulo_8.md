
Capítulo 8
==========

Nesse capítulo você aprenderá funções diversas do PHP, diferente dos
outros capítulos a dinâmica desse será um pouco diferente, pois não
abordaremos um tópico específico. A ideia desse capítulo é mostrar de
uma forma geral a maioria das principais funções do PHP.

substr()
--------

O substr() é uma função que serve para pegar um determinado pedaço da
string. Ela é muito útil quando temos um arquivo .txt ou .csv e
precisamos ler um layout de arquivo e exportar para um banco de dados
por exemplo.

1.  ...

2.  &lt;h1&gt;substr()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$string = 'Mussum ipsum cacilds, vidis litro abertis. fonte:
    http://mussumipsum.com/';

6.  7.  \$subString1 = substr(\$string, 0, 5); //Mussum;

8.  \$subString2 = substr(\$string, 27, 13); //litro abertis

9.  10. echo \$string . '&lt;br /&gt;&lt;br /&gt;';

11. echo 'Primeira substring: ' . \$subString1 . '&lt;br /&gt;';

12. echo 'Segunda substring: ' . \$subString2 . '&lt;br /&gt;';

13. 14. echo '&lt;br /&gt;&lt;br /&gt;';

15. 16. \$arquivo = '../Cap7/novo\_arquivo.txt';

17. if (file\_exists(\$arquivo)) {

18. \$arquivo = fopen(\$arquivo, 'r');

19. \$linha = fgets(\$arquivo);

20. 21. echo htmlentities(\$linha) . '&lt;br /&gt;';

22. \$subString3 = substr(\$linha, 24, 8); //Arquivo

23. echo 'Terceira substring: ' . \$subString3 . '&lt;br /&gt;';

24. } else {

25. echo 'Erro: Arquivo não encontrado.&lt;br /&gt;';

26. }

27. 28. ?&gt; ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/substr.php, no browser
digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/substr.php)[*substr*](http://localhost/PHPBasico/Cap8/substr.php)[*.php*](http://localhost/PHPBasico/Cap8/substr.php).

strlen()
--------

Essa função conta a quantidade de caracteres de uma string.

1.  ...

2.  &lt;h1&gt;strlen()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$string = 'Mussum ipsum cacilds, vidis litro abertis. fonte:
    http://mussumipsum.com/';

6.  7.  echo \$string;

8.  echo '&lt;br /&gt;Essa string tem &lt;strong&gt;' .
    strlen(\$string) . '&lt;/strong&gt; caracteres';

9.  ?&gt;

10. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/strlen.php, no browser
digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/substr.php)[*strlen*](http://localhost/PHPBasico/Cap8/substr.php)[*.php*](http://localhost/PHPBasico/Cap8/substr.php).

count()
-------

Essa função conta a quantidades de elementos de um array ou objeto.

1.  ...

2.  &lt;h1&gt;count()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$array = \['Pera', 'Uva', 'Maça', 'Mamão'\];

6.  7.  var\_dump(\$array);

8.  echo '&lt;br /&gt;Essa array contém &lt;strong&gt;' .
    count(\$array) . '&lt;/strong&gt; itens';

9.  10. ?&gt;

11. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/count.php, no browser
digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/count.php)[*count*](http://localhost/PHPBasico/Cap8/count.php)[*.php*](http://localhost/PHPBasico/Cap8/count.php).

trim()
------

Essa função tira os espaços em branco antes e depois da string. Ela é
muito utilizada em campos vindos de formulários.

nl2br()
-------

Essa função insere quebras de linha HTML antes de todas newlines em uma
string, também utilizada em campos vindos de formulários.

crypt(), md5(), sha1() e base64\_encode()
-----------------------------------------

Essas funções são geralmente utilizadas para hash, senhas ou qualquer
coisa que precisa ser criptografada.

1.  ...

2.  &lt;h1&gt;crypt(), md5(), sha1() e base64\_encode()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$string = '123456789';

6.  7.  echo 'A string &lt;strong&gt;' . \$string . '&lt;/strong&gt;
    usando a função &lt;strong&gt;crypt()&lt;/strong&gt; é exibida
    assim: &lt;strong&gt;' . crypt(\$string) . '&lt;/strong&gt;. &lt;br
    /&gt;';

8.  echo 'A string &lt;strong&gt;' . \$string . '&lt;/strong&gt; usando
    a função &lt;strong&gt;md5()&lt;/strong&gt; é exibida assim:
    &lt;strong&gt;' . md5(\$string) . '&lt;/strong&gt;. &lt;br /&gt;';

9.  echo 'A string &lt;strong&gt;' . \$string . '&lt;/strong&gt; usando
    a função &lt;strong&gt;sha1()&lt;/strong&gt; é exibida assim:
    &lt;strong&gt;' . sha1(\$string) . '&lt;/strong&gt;. &lt;br /&gt;';

10. echo 'A string &lt;strong&gt;' . \$string . '&lt;/strong&gt; usando
    a função &lt;strong&gt;base64\_encode()&lt;/strong&gt; é exibida
    assim: &lt;strong&gt;' . base64\_encode(\$string) .
    '&lt;/strong&gt;. &lt;br /&gt;';

11. ?&gt;

12. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/criptografia.php, no
browser digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/count.php)[*criptografia*](http://localhost/PHPBasico/Cap8/count.php)[*.php*](http://localhost/PHPBasico/Cap8/count.php).

ucwords(), strtolower() e strtoupper()
--------------------------------------

Essas funções controlam como a string será exbida. A *ucwords()*
converte somente as primeiras letras em maiúsculo, a *strtolower()*
converte toda a string para minúsculo e a *strtoupper()* converte toda a
string para maiúsculo.

1.  ...

2.  &lt;h1&gt;ucwords(), strtolower() e strtoupper()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$string = 'Mussum ipsum cacilds, vidis litro abertis. fonte:
    http://mussumipsum.com/';

6.  7.  echo \$string . '&lt;br /&gt;&lt;br /&gt;';

8.  echo 'usando a função &lt;strong&gt;ucwords()&lt;/strong&gt;: ' .
    ucwords(\$string) . '&lt;br /&gt;';

9.  echo 'usando a função &lt;strong&gt;strtolower()&lt;/strong&gt;: ' .
    strtolower(\$string) . '&lt;br /&gt;';

10. echo 'usando a função &lt;strong&gt;strtoupper()&lt;/strong&gt;: ' .
    strtoupper(\$string) . '&lt;br /&gt;';

11. 12. ?&gt;

13. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/trataString.php, no
browser digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/count.php)[*trataString*](http://localhost/PHPBasico/Cap8/count.php)[*.php*](http://localhost/PHPBasico/Cap8/count.php).

date()
------

Essa função formata a data e a hora local (servidor). Essa função é
muito poderosa, pois é possível montar um calendário completo, fazer
conversões e junto com outras funções exclusivas para data podemos fazer
diversos cálculos. Veja as possíveis opções de exibição no quadro
abaixo.

  Caractere de format    Descrição                                                                                                                                                                                    Exemplo de valores retornados
  ---------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------
  *Day*                  ---                                                                                                                                                                                          ---
  *d*                    Dia do mês, 2 digitos com preenchimento de zero                                                                                                                                              *01* até *31*
  *D*                    Uma representação textual de um dia, três letras                                                                                                                                             *Mon* até *Sun*
  *j*                    Dia do mês sem preenchimento de zero                                                                                                                                                         *1* até *31*
  *l* ('L' minúsculo)    A representação textual completa do dia da semana                                                                                                                                            *Sunday* até *Saturday*
  *N*                    Representação numérica ISO-8601 do dia da semana (adicionado no PHP 5.1.0)                                                                                                                   *1* (para Segunda) até *7* (para Domingo)
  *S*                    Sufixo ordinal inglês para o dia do mês, 2 caracteres                                                                                                                                        *st*, *nd*, *rd* ou *th*. Funciona bem com *j*
  *w*                    Representação numérica do dia da semana                                                                                                                                                      *0* (para domingo) até *6* (para sábado)
  *z*                    O dia do ano (começando do 0)                                                                                                                                                                *0* through *365*
  ***Semana***           **---**                                                                                                                                                                                      **---**
  *W*                    Número do ano da semana ISO-8601, semanas começam na Segunda (adicionado no PHP 4.1.0)                                                                                                       Exemplo: *42* (the 42nd week in the year)
  *Mês*                  ---                                                                                                                                                                                          ---
  *F*                    Um representação completa de um mês, como January ou March                                                                                                                                   *January* até *December*
  *m*                    Representação numérica de um mês, com leading zeros                                                                                                                                          *01* a *12*
  *M*                    Uma representação textual curta de um mês, três letras                                                                                                                                       *Jan* a *Dec*
  *n*                    Representação numérica de um mês, sem leading zeros                                                                                                                                          *1* a *12*
  *t*                    Número de dias de um dado mês                                                                                                                                                                *28* through *31*
  ***Year***             **---**                                                                                                                                                                                      **---**
  *L*                    Se está em um ano bissexto                                                                                                                                                                   *1* se está em ano bissexto, *0* caso contrário.
  *o*                    Número do ano ISO-8601. Este tem o mesmo valor como *Y*, exceto que se o número da semana ISO (*W*) pertence ao anterior ou próximo ano, o ano é usado ao invés. (adicionado no PHP 5.1.0)   Exemplos: *1999* ou *2003*
  *Y*                    Uma representação de ano completa, 4 dígitos                                                                                                                                                 Exemplos: *1999* ou *2003*
  *y*                    Uma representação do ano com dois dígitos                                                                                                                                                    Exemplos: *99* ou *03*
  ***Tempo***            **---**                                                                                                                                                                                      **---**
  *a*                    Antes/Depois de meio-dia em minúsculo                                                                                                                                                        *am* or *pm*
  *A*                    Antes/Depois de meio-dia em maiúsculo                                                                                                                                                        *AM* or *PM*
  *B*                    Swatch Internet time                                                                                                                                                                         *000* até *999*
  *g*                    Formato 12-horas de uma hora sem preenchimento de zero                                                                                                                                       *1* até *12*
  *G*                    Formato 24-horas de uma hora sem preenchimento de zero                                                                                                                                       *0* até *23*
  *h*                    Formato 12-horas de uma hora com zero preenchendo à esquerda                                                                                                                                 *01* até *12*
  *H*                    Formato 24-horas de uma hora com zero preenchendo à esquerda                                                                                                                                 *00* até *23*
  *i*                    Minutos com zero preenchendo à esquerda                                                                                                                                                      *00* até *59*
  *s*                    Segundos, com zero preenchendo à esquerda                                                                                                                                                    *00* até *59*
  *u*                    Milisegundos (adicionado no PHP 5.2.2)                                                                                                                                                       Exemplo: *54321*
  ***Timezone***         **---**                                                                                                                                                                                      **---**
  *e*                    Identificador de Timezone (adicionado no PHP 5.1.0)                                                                                                                                          Exemplos: *UTC*, *GMT*, *Atlantic/Azores*
  *I* (capital i)        Se a data está ou não no horário de verão                                                                                                                                                    *1* se horário de verão, *0* caso contrário.
  *O*                    Diferença para Greenwich time (GMT) em horas                                                                                                                                                 Exemplo: *+0200*
  *P*                    Diferença para Greenwich time (GMT) com dois pontos entre horas e minutos (adicionado no PHP 5.1.3)                                                                                          Exemplo: *+02:00*
  *T*                    Abreviação de Timezone                                                                                                                                                                       Exemplos: *EST*, *MDT* ...
  *Z*                    Timezone offset in seconds. The offset for timezones west of UTC is always negative, and for those east of UTC is always positive.                                                           *-43200* até *50400*
  ***Full Date/Time***   **---**                                                                                                                                                                                      **---**
  *c*                    ISO 8601 date (adicionado no PHP 5)                                                                                                                                                          2004-02-12T15:19:21+00:00
  *r*                    [» RFC 2822](http://www.faqs.org/rfcs/rfc2822) formatted date                                                                                                                                Exemplo: *Thu, 21 Dec 2000 16:01:07 +0200*
  *U*                    Segundos desde a Época Unix (January 1 1970 00:00:00 GMT)                                                                                                                                    Veja também [time()](http://php.net/manual/pt_BR/function.time.php)

1.  ...

2.  &lt;h1&gt;date()&lt;/h1&gt;

3.  4.  &lt;?php

5.  echo 'Data e hora padrão de banco de dados &lt;strong&gt;' .
    date('Y-m-d H:i:s') . '&lt;/strong&gt;&lt;br /&gt;';

6.  echo 'Data e hora padrão europeu &lt;strong&gt;' .
    date('d/m/Y H:i:s') . '&lt;/strong&gt;&lt;br /&gt;';

7.  echo 'Data com ano com 2 dígitos &lt;strong&gt;' . date('d/m/y') .
    '&lt;/strong&gt;&lt;br /&gt;';

8.  echo 'Somente hora &lt;strong&gt;' . date('H:i:s') .
    '&lt;/strong&gt;&lt;br /&gt;';

9.  echo 'Mês por extenso &lt;strong&gt;' . date('F') .
    '&lt;/strong&gt;&lt;br /&gt;';

10. echo 'Mês com 3 letras &lt;strong&gt;' . date('M') .
    '&lt;/strong&gt;&lt;br /&gt;';

11. echo 'Semana do ano &lt;strong&gt;' . date('W') .
    '&lt;/strong&gt;&lt;br /&gt;';

12. ?&gt;

13. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/date.php, no browser
digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/count.php)[*date*](http://localhost/PHPBasico/Cap8/count.php)[*.php*](http://localhost/PHPBasico/Cap8/count.php).

checkdate()
-----------

Essa função verifica se uma data fornecida é verdadeira ou falsa.

1.  ...

2.  &lt;h1&gt;checkdate()&lt;/h1&gt;

3.  4.  &lt;?php

5.  echo 'Data 31/12/2000';

6.  var\_dump(checkdate(12, 31, 2000)); //mês, dia, ano

7.  8.  echo '&lt;br /&gt;Data 29/02/2001';

9.  var\_dump(checkdate(2, 29, 2001)); //mês, dia, ano

10. 11. \$data = date('d/m/Y');

12. echo '&lt;br /&gt;Data ' . \$data;

13. var\_dump(checkdate(substr(\$data, 3, 2), substr(\$data, 0, 2),
    substr(\$data, 7, 4))); //mês, dia, ano

14. ?&gt;

15. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/checkdate.php, no
browser digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/checkdatedate.php)[*check*](http://localhost/PHPBasico/Cap8/checkdatedate.php)[*datedate*](http://localhost/PHPBasico/Cap8/checkdatedate.php)[*.php*](http://localhost/PHPBasico/Cap8/checkdatedate.php).

strtotime()
-----------

Essa função é muito útil para cálculos de data, datas futuras etc. Ela
pega uma data e converte para o padrão timestamp.

1.  ...

2.  &lt;h1&gt;strtotime()&lt;/h1&gt;

3.  4.  &lt;?php

5.  echo strtotime("now"), ' -&gt; ', date('d/m/Y',
    strtotime("now")),'&lt;br /&gt;';

6.  echo strtotime("10 September 2000"), ' -&gt; ', date('d/m/Y',
    strtotime("10 September 2000")),'&lt;br /&gt;';

7.  echo strtotime("+1 day"), ' -&gt; ', date('d/m/Y', strtotime("+1
    day")),'&lt;br /&gt;';

8.  echo strtotime("+1 week"), ' -&gt; ', date('d/m/Y', strtotime("+1
    week")),'&lt;br /&gt;';

9.  echo strtotime("+1 week 2 days 4 hours 2 seconds"), ' -&gt; ',
    date('d/m/Y', strtotime("+1 week 2 days 4 hours 2 seconds")),'&lt;br
    /&gt;';

10. echo strtotime("next Thursday"), ' -&gt; ', date('d/m/Y',
    strtotime("next Thursday")),'&lt;br /&gt;';

11. echo strtotime("last Monday"), ' -&gt; ', date('d/m/Y',
    strtotime("last Monday")),'&lt;br /&gt;';

12. echo date("jS F, Y", strtotime("11/12/10"));

13. ?&gt;

14. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/strtotime.php, no
browser digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/strtotime.php)[*strtotime*](http://localhost/PHPBasico/Cap8/strtotime.php)[*.php*](http://localhost/PHPBasico/Cap8/strtotime.php).

str\_replace()
--------------

Essa função faz substituição de caracteres, strings inteiras ou
elementos de array.

1.  ...

2.  &lt;h1&gt;str\_replace()&lt;/h1&gt;

3.  4.  &lt;?php

5.  //substituição com string

6.  \$string = 'O gato roeu a roupa do rei de Roma.';

7.  \$novaString = str\_replace('gato', 'rato', \$string);

8.  echo \$novaString . '&lt;br /&gt;&lt;br /&gt;';

9.  10. //substituição com arrays

11. \$frase = "você comeria frutas, vegetais, e fibra todos os dias.";

12. \$saudavel = array("frutas", "vegetais", "fibra");

13. \$saboroso = array("pizza", "cerveja", "sorvete");

14. \$novafrase = str\_replace(\$saudavel, \$saboroso, \$frase);

15. echo \$novafrase;

16. ?&gt; ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/strReplace.php, no
browser digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/strReplace)[*st*](http://localhost/PHPBasico/Cap8/strReplace)[*rReplace*](http://localhost/PHPBasico/Cap8/strReplace)*.*[*php*](http://localhost/PHPBasico/Cap8/strtotime.php).

preg\_replace()
---------------

Parecida com a função *str\_replace()*, essa função faz substituições
utilizando expressões regulares.

1.  ...

2.  &lt;h1&gt;preg\_replace()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$cpf = '234.144.675/26';

6.  \$cpf = preg\_replace("/\[\^0-9\]/", "", \$cpf);

7.  // O /.../ indica um intervalo, o \^ sgnifica negação, \[0-9\]
    somente número.

8.  // Ou seja, substitua qualquer coisa que não seja número por nada.

9.  echo 'CPF: ' . \$cpf . '&lt;br /&gt;&lt;br /&gt;';

10. 11. \$string1 = "Copyright 1999 - 2015";

12. \$string1 = preg\_replace("(\[0-9\]+)", "2000", \$string1);

13. // O (...) indica uma expressão. Substitua qualquer expressão
    numérica para 2000.

14. echo \$string1 . '&lt;br /&gt;&lt;br /&gt;';

15. 16. \$string1 = 'Abril 15, 2003';

17. \$pattern = '/(\\w+) (\\d+), (\\d+)/i';

18. // \\w indica os caracteres alfa (letras), \\d equivalente ao
    \[0-9\], \\i case insensitive

19. \$replacement = '\${1} 1, \$3';

20. echo preg\_replace(\$pattern, \$replacement, \$string1) . '&lt;br
    /&gt;&lt;br /&gt;';

21. 22. \$string2 = "Entre em contato comigo no email email@email.com,

23. responderei quando puder.";

24. \$string2 = preg\_replace('/@(\[-\\.0-9a-zA-Z\]+)/', '@…',
    \$string2);

25. 26. echo \$string2;

27. ?&gt;

28. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/pregReplace.php, no
browser digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/pregReplace.php)[*preg*](http://localhost/PHPBasico/Cap8/pregReplace.php)[*Replace.*](http://localhost/PHPBasico/Cap8/pregReplace.php)[*php*](http://localhost/PHPBasico/Cap8/pregReplace.php).

**Nota:** Expressão regula é um assunto muito vasto e complexo, para
poder entender melhor, vale muito a pena a leitura desse material da
DevMedia:
**http://www.devmedia.com.br/expressoes-regulares-em-php/25076**

explode()
---------

Essa função, como o nome sugere explode uma string de acordo com uma
regra (delimitador). Ela é muito útil quando temos um arquivo .csv e
precisamos separar palavas ou textos que contenham algum delimitador
como a virgula ou ponto e virgula.

1.  ...

2.  &lt;h1&gt;explode()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$str = 'carro|moto|bike|ônibus';

6.  7.  \$string1 = explode('|', \$str); //explode a string inteira

8.  var\_dump(\$string1);

9.  10. \$string2 = explode('|', \$str, 3); //explode somente até a
    terceira ocorrência

11. var\_dump(\$string2);

12. ?&gt;

13. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/explode.php, no browser
digite*
[http://localhost/PHPBasico/Cap8/explode](http://localhost/PHPBasico/Cap8/explode.php)[*.*](http://localhost/PHPBasico/Cap8/explode.php)[*php*](http://localhost/PHPBasico/Cap8/explode.php).

str\_word\_count()
------------------

Essa função, como nome sugere, conta palavras em uma string.

1.  ...

2.  &lt;h1&gt;str\_word\_count()&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$string = 'Mussum ipsum cacilds, vidis litro abertis. fonte:
    http://mussumipsum.com/';

6.  7.  echo \$string;

8.  echo '&lt;br /&gt;Essa string tem &lt;strong&gt;' .
    str\_word\_count(\$string) . '&lt;/strong&gt; palavras';

9.  var\_dump(str\_word\_count(\$string, 1)); // retorna um array
    contendo todas as palavras encontradas dentro de string

10. var\_dump(str\_word\_count(\$string, 2)); // retorna um array
    associativo, onde a chave é a posição numérica da palavra

11. //dentro da string e o valor é a própria palavra.

12. ?&gt;

13. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap8/strWordCount.php, no
browser digite*
[http://localhost/PHPBasico/Cap8/](http://localhost/PHPBasico/Cap8/strWordCount.php)[*strWordCount*](http://localhost/PHPBasico/Cap8/strWordCount.php)[*.*](http://localhost/PHPBasico/Cap8/strWordCount.php)[*php*](http://localhost/PHPBasico/Cap8/strWordCount.php).

Resumo do Capítulo
------------------

Nesse capítulo aprendemos algumas funções importantes do PHP, elas são
apenas uma pequena fração das funções existentes. Para conhecer mais
sobre as funções acesse o site [www.php.net](http://www.php.net/). Essa
sempre será sua principal referência.
