
Capítulo 10
===========

Nesse capítulo você aprenderá os conceitos iniciais de Orientação a
Objetos (OO). A ideia aqui é somente apresentar o que é uma classe, não
nos aprofundar no assunto. Pois é um assunto muito vasto e complexo que
envolve muitos padrões de desenvolvimento. Aqui é só um gancho para o
próximo curso, **PHP do Jeito Certo com Orientação a Objetos**.

1.  &lt;?php

2.  class Pessoa

3.  {

4.  public \$nome;

5.  public \$idade;

6.  public \$sexo;

7.  8.  public function \_\_construct(\$nome, \$idade, \$sexo)

9.  {

10. \$this-&gt;nome = \$nome;

11. \$this-&gt;idade = \$idade;

12. \$this-&gt;\$sexo = \$sexo;

13. }

14. 15. public function comer(\$alimento, \$qtd = 0)

16. {

17. echo utf8\_decode(\$this-&gt;nome . ' esta comendo ' . \$alimento .
    '&lt;br /&gt;&lt;br /&gt;');

18. 19. for (\$i=1; \$qtd &gt;= \$i; \$i++) {

20. echo utf8\_decode(\$this-&gt;nome . ' comeu ' . \$i . ' ' .
    \$alimento . '(s)&lt;br /&gt;');

21. }

22. }

23. }

24. 25. \$pessoa = new Pessoa('Cálcio', 35, 'Masculino');

26. 27. echo \$pessoa-&gt;comer('Maça', 5);

28. 

*Salve em /home/seu\_usuario/www/PHPBasico/Cap10/Pessoa.php, no browser
digite*
[http://localhost/PHPBasico/Cap10/](http://localhost/PHPBasico/Cap10/Pessoa.php)[*Pessoa*](http://localhost/PHPBasico/Cap10/Pessoa.php)[*.*](http://localhost/PHPBasico/Cap10/Pessoa.php)[*php*](http://localhost/PHPBasico/Cap10/Pessoa.php).

Por convenção uma classe deve sempre começar com letra maiúscula e ser
no singular, e o nome do arquivo ser o mesmo nome da classe. Um método
deve ser no padrão ***camelCased***, e deve ser um verbo e/ou
representar uma ação. As propriedades seguem o padrão das variáveis do
PHP, ***camelCased*** seja ou separada por underline.

Para verificar essas convenções acesse o site
**http://www.php-fig.org/** e procure por **PSR-1** e **PSR-2**.

Resumo do capítulo
------------------

Nesse capítulo aprendemos um pouco sobre classes e uma breve introdução
a Programação Orientada a Objetos. No próximo curso **PHP do Jeito Certo
com Orientação a Objetos**, você aprenderá de fato os conceitos e como
criar uma aplicação Orientada a Objetos.
