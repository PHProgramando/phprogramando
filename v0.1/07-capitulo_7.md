
Capítulo 7
==========

Nesse capítulo você aprenderá como trabalhar com diretórios e arquivos
no PHP. No capítulo anterior, criamos um formulário para envio de
arquivos para o servidor, mas o PHP é muito mais poderoso que isso,
podemos manipular os diretórios como fazemos no mundo Linux.

Listar diretórios e arquivos
----------------------------

O PHP possui funções internas que permite ler a estrutura diretórios do
servidor (desde que possuam a devida permissão). Criaremos um script
para exibição de diretórios do servidor.

getcwd(), chdir(), dir() e scandir()
------------------------------------

1.  ...

2.  &lt;h1&gt;Listagem de diretórios&lt;/h1&gt;

3.  4.  &lt;h2&gt;getcwd(), exibe o diretório atual&lt;/h2&gt;

5.  &lt;?= getcwd() ?&gt;

6.  7.  &lt;h2&gt;chdir(), muda o diretório atual&lt;/h2&gt;

8.  &lt;?php

9.  echo getcwd() . '&lt;br /&gt;';

10. chdir('../Cap6');

11. echo getcwd() . '&lt;br /&gt;';

12. chdir('upload');

13. echo getcwd() . '&lt;br /&gt;';

14. ?&gt;

15. 16. &lt;h2&gt;dir(), lista diretórios como uma lista&lt;/h2&gt;

17. &lt;?php

18. \$dir = dir('/var/');

19. echo "Caminho: " . \$dir-&gt;path . "\\n&lt;br /&gt;";

20. 21. /\* Esta é a forma correta de varrer o diretório \*/

22. while (false !== (\$item = \$dir-&gt;read())) {

23. echo \$item."\\n&lt;br /&gt;";

24. }

25. 26. \$dir-&gt;close();

27. ?&gt;

28. 29. &lt;h2&gt;scandir(), lista diretórios como array&lt;/h2&gt;

30. &lt;?php

31. \$dir = scandir('/var/');

32. var\_dump(\$dir);

33. ?&gt;

34. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/listarDiretorios.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/listarDiretorios.php)[7](http://localhost/PHPBasico/Cap7/listarDiretorios.php)[/](http://localhost/PHPBasico/Cap7/listarDiretorios.php)[*listarDiretorios*](http://localhost/PHPBasico/Cap7/listarDiretorios.php)[*.php*](http://localhost/PHPBasico/Cap7/listarDiretorios.php)*.*

Criar, renomear, mover e deletar diretórios
-------------------------------------------

Além da leitura podemos também criar, renomear, mover e excluir
diretórios, desde que se tenha permissão para isso no servidor.

### Criar um diretório

1.  ...

2.  &lt;h1&gt;Criar diretórios&lt;/h1&gt;

3.  &lt;h2&gt;mkdir(), cria um diretório&lt;/h2&gt;

4.  &lt;?php

5.  mkdir('novo\_dir', 0777); // Cria uma nova pasta dentro do diretório
    atual

6.  ?&gt;

7.  ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/criarDiretorios.php, no
browser digite*
[http://localhost/PHPBasico/Cap7/](http://localhost/PHPBasico/Cap7/listarDiretorios.php)[cri](http://localhost/PHPBasico/Cap7/listarDiretorios.php)[*arDiretorios*](http://localhost/PHPBasico/Cap7/listarDiretorios.php)[*.php*](http://localhost/PHPBasico/Cap7/listarDiretorios.php)*.*

### Renomear um diretório

1.  ...

2.  &lt;h1&gt;Renomear diretórios&lt;/h1&gt;

3.  4.  &lt;h2&gt;rename(), muda o nome do diretório ou move um
    diretório&lt;/h2&gt;

5.  &lt;?php

6.  //mkdir('novo\_dir', 0777);

7.  rename('novo\_dir/', 'teste/');

8.  ?&gt;...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/renomearDiretorios.php,
no browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/renomearDiretorios.php)[7](http://localhost/PHPBasico/Cap7/renomearDiretorios.php)[/](http://localhost/PHPBasico/Cap7/renomearDiretorios.php)[renomear](http://localhost/PHPBasico/Cap7/renomearDiretorios.php)[*Diretorios*](http://localhost/PHPBasico/Cap7/renomearDiretorios.php)[*.php*](http://localhost/PHPBasico/Cap7/renomearDiretorios.php)*.*

### Deletar um diretório

1.  ...

2.  &lt;h1&gt;Deletar diretórios&lt;/h1&gt;

3.  4.  &lt;h2&gt;rmdir(), apaga um diretório&lt;/h2&gt;

5.  &lt;?php

6.  //mkdir('novo\_dir', 0777);

7.  //rename('novo\_dir/', 'teste/');

8.  rmdir('teste/');

9.  ?&gt;

10. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/deletarDiretorios.php,
no browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/deletarDiretorios.php)[7](http://localhost/PHPBasico/Cap7/deletarDiretorios.php)[/](http://localhost/PHPBasico/Cap7/deletarDiretorios.php)[dele](http://localhost/PHPBasico/Cap7/deletarDiretorios.php)[*tarDiretorios*](http://localhost/PHPBasico/Cap7/deletarDiretorios.php)[*.php*](http://localhost/PHPBasico/Cap7/deletarDiretorios.php).

**Nota:** Em todos os casos, podemos nos referenciar aos endereços dos
diretórios como: './nome\_do\_diretorio' ou usando o caminho completo,
algo como '/home/seu\_usuário/www/PHPBasico/Cap7/nome\_do\_diretorio'.

Criar arquivos
--------------

Assim como podemos criar diretórios pelo PHP, podemos criar arquivos.
Vamos a um exemplo prático.

fopen(), fwrite(), fclose()
---------------------------

1.  ...

2.  &lt;h1&gt;Criar arquivos&lt;/h1&gt;

3.  4.  &lt;h2&gt;fopen(), cria um arquivo se não existir ou abre um
    arquivo existente&lt;/h2&gt;

5.  &lt;?php

6.  \$criaArquivo = fopen('novo\_arquivo.txt', 'x'); //Cria o arquivo
    novo\_arquivo.txt com permissao de escrita

7.  ?&gt;

8.  9.  &lt;h2&gt;fwrite(), escreve no arquivo criado ou
    aberto&lt;/h2&gt;

10. &lt;?php

11. \$escreve = fwrite(\$criaArquivo, 'Texto a ser inserido no arquivo.
    Pode ser substituído por uma variável contendo um texto longo');

12. ?&gt;

13. 14. &lt;h2&gt;fclose(), fecha o arquivo criado ou aberto&lt;/h2&gt;

15. &lt;?php

16. fclose(\$criaArquivo);

17. ?&gt;

18. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/criaArquivo1.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/criarArquivos.php)[7](http://localhost/PHPBasico/Cap7/criarArquivos.php)[/](http://localhost/PHPBasico/Cap7/criarArquivos.php)[*criaArquivo*](http://localhost/PHPBasico/Cap7/criarArquivos.php)[*1*](http://localhost/PHPBasico/Cap7/criarArquivos.php)[*.php*](http://localhost/PHPBasico/Cap7/criarArquivos.php).

Para usar o fopen() precisamos que o segundo argumento da função informe
qual vai ser o tipo de permissão do arquivo. Veja na tabela abaixo quais
são os tipos suportados.

  Modo     Descrição
  -------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  *'r'*    Abre somente para leitura; coloca o ponteiro do arquivo no começo do arquivo.
  *'r+'*   Abre para leitura e escrita; coloca o ponteiro do arquivo no começo do arquivo.
  *'w'*    Abre somente para escrita; coloca o ponteiro do arquivo no começo do arquivo e reduz o comprimento do arquivo para zero. Se o arquivo não existir, tenta criá-lo.
  *'w+'*   Abre para leitura e escrita; coloca o ponteiro do arquivo no começo do arquivo e reduz o comprimento do arquivo para zero. Se o arquivo não existir, tenta criá-lo.
  *'a'*    Abre somente para escrita; coloca o ponteiro do arquivo no final do arquivo. Se o arquivo não existir, tenta criá-lo.
  *'a+'*   Abre para leitura e escrita; coloca o ponteiro do arquivo no final do arquivo. Se o arquivo não existir, tenta criá-lo.
  *'x'*    Cria e abre o arquivo somente para escrita; coloca o ponteiro no começo do arquivo. Se o arquivo já existir, a chamada a **fopen()** falhará, retornando FALSE e gerando um erro de nível E\_WARNING. Se o arquivo não existir, tenta criá-lo. Isto é equivalente a especificar as flags *O\_EXCL|O\_CREAT* para a chamada de sistema *open(2)*.
  *'x+'*   Cria e abre o arquivo para leitura e escrita; coloca o ponteiro no começo do arquivo. Se o arquivo já existir, a chamada a **fopen()** falhará, retornando FALSE e gerando um erro de nível E\_WARNING. Se o arquivo não existir, tenta criá-lo. Isto é equivalente a especificar as flags *O\_EXCL|O\_CREAT* para a chamada de sistema *open(2)*.

No nosso exemplo, usamos o “x” que indica cria e abre um arquivo e caso
exista ele acusa um erro. Para validar o que o quadro informa, rode
novamente o scripit anterior. *No browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/criarArquivos.php)[7](http://localhost/PHPBasico/Cap7/criarArquivos.php)[/](http://localhost/PHPBasico/Cap7/criarArquivos.php)[*criaArquivo*](http://localhost/PHPBasico/Cap7/criarArquivos.php)[*1*](http://localhost/PHPBasico/Cap7/criarArquivos.php)[*.php*](http://localhost/PHPBasico/Cap7/criarArquivos.php).

Perceba que foi exibido um erro.

**Nota:** Sempre que utilizarmos a função fopen() no final do processo
precisamos fazer o fechamento do arquivo com o fclose().

Criando um novo arquivo pegando um conteúdo externo
---------------------------------------------------

1.  ...

2.  &lt;h1&gt;Cria arquivo pegando conteúdo externo&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$conteudoExterno = file\_get\_contents('criaArquivo1.php'); //Pega
    o conteúdo do arquivo

6.  7.  if (@\$arquivo = fopen('novo\_arquivo1.txt', 'x')) {

8.  if (fwrite(\$arquivo, \$conteudoExterno)) {

9.  echo 'Conteúdo inserido no arquivo com sucesso.&lt;br /&gt;';

10. } else {

11. echo 'Erro: Não foi possível gravar o conteúdo no arquivo.&lt;br
    /&gt;';

12. }

13. 14. fclose(\$arquivo);

15. } else {

16. echo 'Erro: Não foi possível criar o arquivo.&lt;br /&gt;';

17. }

18. ?&gt;

19. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/criaArquivo2.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/criaArquivo2.php)[7](http://localhost/PHPBasico/Cap7/criaArquivo2.php)[/](http://localhost/PHPBasico/Cap7/criaArquivo2.php)[*criaArquivo*](http://localhost/PHPBasico/Cap7/criaArquivo2.php)[*2*](http://localhost/PHPBasico/Cap7/criaArquivo2.php)[*.php*](http://localhost/PHPBasico/Cap7/criaArquivo2.php).

Mais uma vez utilizamos o tipo de abertura de arquivo como “x”, execute
novamente o arquivo e veja que depois do tratamento, é exibida uma
mensagem de erro mais amigável.

Lendo arquivos
--------------

Podemos ler os arquivos com a função fgets(). Essa função lê a primeira
linha do arquivo. Podemos ler também uma quantidade X de bytes de uma
linha e para ler todo um arquivo podemos usa a função
file\_get\_contents().

ftegs(), Ler arquivo simples
----------------------------

1.  ...

2.  &lt;h1&gt;fgets(), ler arquivo simples&lt;/h1&gt;

3.  4.  &lt;?php

5.  if (\$arquivo = fopen('novo\_arquivo1.txt', 'r')) {

6.  \$linha = fgets(\$arquivo);

7.  8.  echo htmlentities(\$linha1); // lê a primeira linha do arquivo
    exibe

9.  10. fclose(\$arquivo);

11. } else {

12. echo 'Erro: Não foi possível ler o arquivo.&lt;br /&gt;';

13. }

14. ?&gt;

15. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/lerArquivo1.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[7](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[/](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[ler](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[*Arquivo*](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[*1*](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[*.php*](http://localhost/PHPBasico/Cap7/lerArquivo1.php).

fgets(), ler arquivo por bytes
------------------------------

1.  ...

2.  &lt;h1&gt;fgets(), ler arquivo por byte&lt;/h1&gt;

3.  4.  &lt;?php

5.  if (\$arquivo = fopen('novo\_arquivo1.txt', 'r')) {

6.  \$linha = fgets(\$arquivo, 16);

7.  8.  echo htmlentities(\$linha); // lê a primeira linha do arquivo
    exibe

9.  10. fclose(\$arquivo);

11. } else {

12. echo 'Erro: Não foi possível ler o arquivo.&lt;br /&gt;';

13. }

14. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/lerArquivo2.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[7](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[/](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[ler](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[*Arquivo*](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[*2*](http://localhost/PHPBasico/Cap7/lerArquivo1.php)[*.php*](http://localhost/PHPBasico/Cap7/lerArquivo1.php).

fgets(), ler todo o arquivo com um loop
---------------------------------------

1.  ...

2.  &lt;h1&gt;fgets(), lendo todo o arquivo com loop&lt;/h1&gt;

3.  4.  &lt;?php

5.  if (\$arquivo = fopen('novo\_arquivo1.txt', 'r')) {

6.  while (!feof(\$arquivo)) {

7.  \$linha = fgets(\$arquivo);

8.  echo htmlentities(\$linha) . '&lt;br /&gt;';

9.  }

10. 11. fclose(\$arquivo);

12. } else {

13. echo 'Erro: Não foi possível ler o arquivo.&lt;br /&gt;';

14. }

15. ?&gt;

16. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/lerArquivo3.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/lerArquivo3.php)[7](http://localhost/PHPBasico/Cap7/lerArquivo3.php)[/](http://localhost/PHPBasico/Cap7/lerArquivo3.php)[ler](http://localhost/PHPBasico/Cap7/lerArquivo3.php)[*Arquivo*](http://localhost/PHPBasico/Cap7/lerArquivo3.php)[*3*](http://localhost/PHPBasico/Cap7/lerArquivo3.php)[*.php*](http://localhost/PHPBasico/Cap7/lerArquivo3.php).

file\_get\_content(), ler todo o arquivo
----------------------------------------

1.  ...

2.  &lt;h1&gt;file\_get\_contents(), lendo todo o arquivo com
    loop&lt;/h1&gt;

3.  4.  &lt;?php

5.  if (\$arquivo = file\_get\_contents('criaArquivo1.php')) {

6.  echo htmlentities(\$arquivo);

7.  } else {

8.  echo 'Erro: Não foi possível ler o arquivo.&lt;br /&gt;';

9.  }

10. ?&gt;

11. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/lerArquivo4.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[7](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[/](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[ler](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[*Arquivo*](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[*4*](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[*.php*](http://localhost/PHPBasico/Cap7/lerArquivo4.php).

Apagando um arquivo
-------------------

Pelo PHP podemos também apagar arquivos usando a função unlink().

unlink(), apaga um arquivo
--------------------------

1.  ...

2.  &lt;h1&gt;unlink(), apaga um arquivo&lt;/h1&gt;

3.  4.  &lt;?php

5.  \$arquivo = 'novo\_arquivo1.txt';

6.  if (file\_exists(\$arquivo)) {

7.  if (unlink(\$arquivo)) {

8.  echo 'Arquivo deletado com sucesso.';

9.  } else {

10. echo 'Erro: Não foi possível deletar o arquivo.';

11. }

12. } else {

13. echo 'Erro: Arquivo não encontrado.&lt;br /&gt;';

14. }

15. ?&gt;

16. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap7/apagarArquivo.php, no
browser digite*
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[7](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[/](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[apagar](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[*Arquivo*](http://localhost/PHPBasico/Cap7/lerArquivo4.php)[*.php*](http://localhost/PHPBasico/Cap7/lerArquivo4.php).

Resumo do Capítulo
------------------

Nesse capítulo aprendemos as funções que manipulam diretórios e
arquivos, vimos desde a listagem de diretórios e arquivos, como também
sua criação e exclusão.

Exercícios
----------

1.  Crie um diretório chamado ***exercicio***;

2.  Crie dois subdiretórios em ***execicio*** simultaneamente chamados
    ***arquivos1*** e ***arquivos2***;

3.  Crie um diretório chamado ***teste*** e o renomeie para
    ***aplicacao***;

4.  Liste todos os diretórios criados;

5.  Apague o diretório ***aplicacao***;

6.  Crie um arquivo chamado ***lorem.txt***, contendo dois parágrafos
    lorem ipsum dentro do diretório ***arquivos1***;

7.  Adicione um terceiro parágrafo ao arquivo ***lorem.txt*** no final
    do arquivo;

8.  Faça uma cópia do arquivo ***lorem.txt*** para ***lorem2.txt*** no
    diretório ***arquivos2***;
