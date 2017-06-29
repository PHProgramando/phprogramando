
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

...
<h1>If</h1>

<?php
    $idade = 18;

    //Testa se usuário tem 18 anos ou mais
    if ($idade >= 18) {
        echo 'Opa, já posso dirigir e beber';
    }
?>
...

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional1.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional1.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional1.php)[*/*](http://localhost/PHPBasico/Cap3/condicional1.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional1.php)[*3*](http://localhost/PHPBasico/Cap3/condicional1.php)[*/*](http://localhost/PHPBasico/Cap3/condicional1.php)[*condicional1*](http://localhost/PHPBasico/Cap3/condicional1.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional1.php).

Nota: Repare que entre o “**if**” e o parênteses “**(**“, existe um
espaço, o mesmo ocorre entre o fechamento do parênteses “**)**” e a
abertura da chaves “**{**“. Não há espaço depois da abertura nem
fechamento das chaves.[^2]

#### else

```
...
<h1>If, Else</h1>

<?php
    $idade = 18;

    //Testa se usuário tem 18 anos ou mais
    if ($idade >= 18) {
        echo 'Opa, já posso dirigir e beber';
    } else {
        //retorna false
        echo 'Não posso dirigir nem beber';
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional2.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional2.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional2.php)[*/*](http://localhost/PHPBasico/Cap3/condicional2.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional2.php)[*3*](http://localhost/PHPBasico/Cap3/condicional2.php)[*/*](http://localhost/PHPBasico/Cap3/condicional2.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional2.php)[*2*](http://localhost/PHPBasico/Cap3/condicional2.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional2.php).

#### If, elseif e else


```
...
<h1>If, Elseif e Else</h1>

<?php
    $idade = 18;

    //Testa se usuário tem 18 anos ou mais
    if ($idade >= 18) {
        //retorna true
        echo 'Opa, já posso dirigir e beber';
    } elseif ($idade >= 12 && $idade <= 17) {
        //retorna true se idade for maior e
        //igual a 17 e menor e igual a 10
        echo 'Não posso dirigir nem beber';
    } else {
        //retorna false
        echo 'Muito criança, não vai nem para escola sozinho';
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional3.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional3.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional3.php)[*/*](http://localhost/PHPBasico/Cap3/condicional3.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional3.php)[*3*](http://localhost/PHPBasico/Cap3/condicional3.php)[*/*](http://localhost/PHPBasico/Cap3/condicional3.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional3.php)[*3*](http://localhost/PHPBasico/Cap3/condicional3.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional3.php).

#### Outro exemplo if e eles

```
...
<h1>If e Else</h1>

<?php
    $cpf = '00000000000001';

    if ($cpf == "00000000000000" ||
        $cpf == "11111111111111" ||
        $cpf == "22222222222222" ||
        $cpf == "33333333333333" ||
        $cpf == "44444444444444" ||
        $cpf == "55555555555555" ||
        $cpf == "66666666666666" ||
        $cpf == "77777777777777" ||
        $cpf == "88888888888888" ||
        $cpf == "99999999999999")
    {
        echo "CPF inválido!";
    } else {
        echo "CPF informado: " . $cpf;
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional4.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional4.php)[*3*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional4.php)[*4*](http://localhost/PHPBasico/Cap3/condicional4.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional4.php).

Veremos agora outra forma de condicional o switch (\$var) … case.

#### Switch

Assim como no if, esse comando fará comparações, e caso o valor seja
verdadeiro, entrará na condição. Vamos a um exemplo bem simples.

```
...
<h1>switch e case</h1>

<?php
    $cor = 'azul';

    switch ($cor) {
        case 'azul':
            echo 'A variável $cor é azul';
            break;
        case 'verde':
            echo 'A variável $cor é verde';
            break;
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional5.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional4.php)[*3*](http://localhost/PHPBasico/Cap3/condicional4.php)[*/*](http://localhost/PHPBasico/Cap3/condicional4.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional4.php)[*5*](http://localhost/PHPBasico/Cap3/condicional4.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional4.php).

Note que no final de cada case exite o comando break, esse comando é
obrigatório, e será explicado em outro exercício.

```
...
<h1>switch e case</h1>

<?php
    $cor = 'verde1';

    switch ($cor) {
        case 'azul':
            echo 'A variável $cor é azul';
            break;
        case 'verde':
            echo 'A variável $cor é verde';
            break;
        default:
            echo 'A variável $cor é preto';
            break;
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/condicional6.php*, no
browser digite
[*http://localhost/*](http://localhost/PHPBasico/Cap3/condicional6.php)[*PHPBasico*](http://localhost/PHPBasico/Cap3/condicional6.php)[*/*](http://localhost/PHPBasico/Cap3/condicional6.php)[*Cap*](http://localhost/PHPBasico/Cap3/condicional6.php)[*3*](http://localhost/PHPBasico/Cap3/condicional6.php)[*/*](http://localhost/PHPBasico/Cap3/condicional6.php)[*condicional*](http://localhost/PHPBasico/Cap3/condicional6.php)[*6*](http://localhost/PHPBasico/Cap3/condicional6.php)[*.php*](http://localhost/PHPBasico/Cap3/condicional6.php).

O comando **default**:, serve como um “**else**”, ou seja, no caso de
false em todos os “**case**” ele assume um valor padrão.

```
...
<h1>switch e case</h1>

<?php
    $beer = 'Colarinho';

    switch ($beer) {
        case 'Coruja':
        case 'ERDINGER':
        case 'Colarinho':
        case 'Paulaner':
            echo 'Ótimas cervejas!';
            break;
        case 'Colorado':
        case 'Rogue':
        case 'Perigosa':
            echo 'Cerveja muito amarga e parece caldo de cana!';
            break;
        default:
            echo 'Prefiro cervejas de trigo!';
            break;
    }
?>
...
```

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


```
...
<h1>While</h1>

<?php
    $contador = 1;
    
    while ($contador <= 10) {
        echo $contador++;
        echo '<br />';
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao1.php*, no
browser digite <http://localhost/PHPBasico/Cap3/repeticao1.php>.

Nota: Assim como no **if** e no **switch**, observe o espaço entre o
comando “**while**” e o parênteses “**(**“ e o espaço entre o fechamento
do parênteses “**)**” com a abertura da chave “**{**“.[^4]

#### Do while

```
...
<h1>Do While</h1>

<?php
    $contador = 10;
    
    do {
        echo \$contador++;
        echo '<br />';
    } while ($contador <= 10);

?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao2.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao1.php)[2](http://localhost/PHPBasico/Cap3/repeticao1.php)[.php](http://localhost/PHPBasico/Cap3/repeticao1.php).

Nota: A diferença entre o **while** e o **do while** é que o **while**
testa se é verdadeiro e executa enquanto o **do while** executa pelo
menos uma vez antes de testar. Veja a forma como foi codificado o **do
while**, segue o mesmo padrão do FIG[^5]

#### For

```
...
<h1>For</h1>

<?php
    for ($i = 1; $i <= 10; $i++) {
        echo $i . '<br />';
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao3.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao1.php)[3](http://localhost/PHPBasico/Cap3/repeticao1.php)[.php](http://localhost/PHPBasico/Cap3/repeticao1.php).

#### For com array

```
...
<h1>For com array</h1>

<?php
    $vetor = array(1, 2, 3, 4, 5);

    for ($i = 0; $i < 5; $i++) {
        $item = $vetor[$i];
        echo $item . '<br />';
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao4.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao4.php)[4](http://localhost/PHPBasico/Cap3/repeticao4.php)[.php](http://localhost/PHPBasico/Cap3/repeticao4.php).

#### Foreach simples

```
...
<h1>Foreach simples</h1>

<?php
    $vetor = array(1, 2, 3, 4, 5);

    foreach ($vetor as $item) {
        echo $item . '<br />';
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap3/repeticao5.php*, no
browser digite
[http://localhost/PHPBasico/Cap3/repeticao](http://localhost/PHPBasico/Cap3/repeticao5.php)[5](http://localhost/PHPBasico/Cap3/repeticao5.php)[.php](http://localhost/PHPBasico/Cap3/repeticao5.php).

#### Foreach chave (key) e valor (value)

```
...
<h1>Foreach chave valor</h1>

<?php
    $motos = [
        1 => 'Suzuki',
        2 => 'Yamaha',
        3 => 'Honda',
        4 => 'Triumph',
        5 => 'Ducati'
    ];

    foreach ($motos as $key => $value) {
        echo $key . ' - ' . $value . '<br />';
    }
?>
...
```

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
