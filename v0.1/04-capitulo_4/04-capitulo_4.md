
Capítulo 4
==========

Nesse capítulo aprenderemos sobre as funções do PHP, e como elas são
muito úteis e evitam a repetição de código. A partir de agora, sairemos
do basicão e entraremos um pouco mais a fundo na linguagem e estamos
dando um passo para o nível intermediário.

Funções
-------

O principal objetivo das funções é simplificar a vida do desenvolvedor.
Aprendendo e usando as ***functions***, você será capaz de implementar o
**DRY** (***Don't Repeat Yourself***). Algumas caraterísticas de uma
função, ela pode ou não esperar um argumento ou mais, e sempre returna
um valor mesmo que nulo. Vamos aos exemplos.

### Função sem argumentos

```
...

<h1>Função sem argumento</h1>

<?php

//declaração da função
function soma()
{
    $valor1 = 20;
    $valor2 = 30;

    echo $valor1 + $valor2;
}

//chamando a função a ser executada
soma();

?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap4/funcao1.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap4/funcao1.php)[4](http://localhost/PHPBasico/Cap4/funcao1.php)[/](http://localhost/PHPBasico/Cap4/funcao1.php)[funcao1](http://localhost/PHPBasico/Cap4/funcao1.php)[.php](http://localhost/PHPBasico/Cap4/funcao1.php).

**Nota:** Em uma função as variáveis criadas dentro dela, só é válida
dentro da própria função. Variáveis criadas fora da função também não
são acessadas pela função somente se utilizar o escopo GLOBALS dentro da
função.

### Função sem argumentos com variável fora do escopo

```
...

<h1>Função sem argumento com variável fora do
    escopo</h1>

<?php
$valor1 = 100;

//declaração da função
function soma()
{
    $valor1 = 20;
    $valor2 = 30;

    echo $valor1 + $valor2;

}

//chamando a função a ser executada
soma();

//valor fora do escopo da função

echo '<br />' . $valor1;

?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap4/funcao2.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap4/funcao1.php)[4](http://localhost/PHPBasico/Cap4/funcao1.php)[/](http://localhost/PHPBasico/Cap4/funcao1.php)[funcao](http://localhost/PHPBasico/Cap4/funcao1.php)[2](http://localhost/PHPBasico/Cap4/funcao1.php)[.php](http://localhost/PHPBasico/Cap4/funcao1.php).

**Nota:** Repare que o valor da soma continuou o mesmo. Isso porque a
variável $valor1 só é utilizada fora da função.

### Função sem argumento com variável global
```
...

<h1>Função sem argumento com variável global</h1>

<?php
$valor1 = 100;

//declaração da função

function soma()
{
    global $valor1;
    $valor2 = 30;

    echo \$valor1 + \$valor2;

}

//chamando a função a ser executada
soma();

//valor fora do escopo da função
 echo '<br />' . $valor1;

?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap4/funcao3.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap4/funcao1.php)[4](http://localhost/PHPBasico/Cap4/funcao1.php)[/](http://localhost/PHPBasico/Cap4/funcao1.php)[funcao](http://localhost/PHPBasico/Cap4/funcao1.php)[3](http://localhost/PHPBasico/Cap4/funcao1.php)[.php](http://localhost/PHPBasico/Cap4/funcao1.php).

**Nota:** Repare que o valor da soma modificou. Isso porque a variável
\$valor1 foi precedida da palavra-chave “global” dentro da função.

### Função com argumento
```
...

<h1>Função com argumento</h1>

<?php

//declaração da função
function exibeNome($nome)
{
    $texto = 'O nome escolhido foi: ' . $nome;

    return $texto;
}

$nome = 'Juraci José';

//chamando a função a ser executada
echo exibeNome($nome);

?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap4/funcao4.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap4/funcao4.php)[4](http://localhost/PHPBasico/Cap4/funcao4.php)[/](http://localhost/PHPBasico/Cap4/funcao4.php)[funcao](http://localhost/PHPBasico/Cap4/funcao4.php)[4](http://localhost/PHPBasico/Cap4/funcao4.php)[.php](http://localhost/PHPBasico/Cap4/funcao4.php).

**Nota:** Observe que nesse exemplo eu passei um argumento para a função
chamada $nome, com isso posso alterar livremente a variável nome sem
ter que mudar a função.

### Função com dois argumentos ou mais
```
...
<h1>Função com dos argumentos ou mais</h1>

<?php

//declaração da função
function exibeNomeIdade($nome, $idade = 100)
{
    $texto = 'O nome escolhido foi: ' . $nome . ' tenho ' . $idade .
    ' anos.';

    return \$texto;
}

$nome = 'Juraci José';
$idade = 27;

//chamando a função a ser executada
echo exibeNomeIdade($nome, $idade);

?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap4/funcao5.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap4/funcao5.php)[4](http://localhost/PHPBasico/Cap4/funcao5.php)[/](http://localhost/PHPBasico/Cap4/funcao5.php)[funcao](http://localhost/PHPBasico/Cap4/funcao5.php)[5.](http://localhost/PHPBasico/Cap4/funcao5.php)[php](http://localhost/PHPBasico/Cap4/funcao5.php).

**Nota:** Nesse exemplo passamos 2 parâmetros, note que **$idade** está
declarado com o valor 100, isso indica que o parâmetro tem um valor
padrão e também quer dizer que pode ser omitido na chamada da função.

Resumo do capítulo
------------------

Nesse capítulo aprendemos como criar e chamar funções. Elas são muito
úteis para evitar reescrita do código. Com as funções você começará a
criar suas próprias bibliotecas e reutilizá-las em outros projetos.

Exercícios
----------

1.  Crie uma função que passe um parâmetro em forma de array contendo
    nome, nota1, nota2, nota3 e nota4, Calcule a média do aluno e exiba
    no final o nome do aluno e a situação se está aprovado, reprovado ou
    em recuperação e a sua média. O critério é o mesmo do exercício 1 do
    Capítulo 3.

2.  Crie uma função que retorne os elementos pares de um loop de
    forma automática.
