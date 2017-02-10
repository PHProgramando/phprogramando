
Capítulo 9
==========

Nesse capítulo você aprenderá as principais e mais conhecidas funções de
banco de dados. Conhecerá um pouco da evolução das bibliotecas de banco
de dados e também como atualmente os profissionais estão trabalhando.

A coisa mais importante quando se está usando banco de dados é criar um
banco de dados e suas tabelas e uma conexão com ele, a partir daí que
podemos fazer nossas consultas, inclusões, alterações e exclusões, essas
quatro operações são chamadas de **CRUD** (***Create, Retrieve/Read,
Update e Delete***).

Criando o banco de dados
------------------------

Vamos a partir de agora criar nosso banco e nossas tabelas. No início do
curso instalamos vários pacotes, um deles foi o MySql Server, MySql
Client e o phpMyAdmin. Vamos usar o phpMyAdmin para criar e administrar
nosso banco de teste. O phpMyAdmin é uma interface web muito simples,
intuitiva e fácil de se utilizar.

1.  Acesse a url
    [http://localhost/phpMyAdmin/](http://localhost/phpmyadmin/) e vamos
    logar com o usuário *root* e senha *toor*;

2.  Clique no botão “Base de dados”;

3.  Na caixa de texto “Create database” coloque o nome
    “curso-php-basico”;

4.  Na caixa ao lado marque a opção: utf8\_general\_ci;

5.  Clique no botão “Criar”

Pronto com isso já criamos nosso banco de dados.

Criando a tabela no banco curso-php-basico
------------------------------------------

1.  Se não estiver logado no phpMyAdmin, se logue com as credenciais do
    banco;

2.  Clique no banco que criamos “curso-php-basico”;

3.  Na tela de criação de tabela, “Create table”, no campo “name” digite
    usuarios e no campo “Number of columns” digite o número 5 e clique
    no botão “Executar”;

4.  Na tela que carregou, apareceram 5 linhas referentes aos 5 campos
    que vamos criar nessa tabela. Os campos que aparecem para o cadastro
    são:

    1.  **Nome** (representa o nome do campo);

    2.  **Tipo** (qual tipo de dados vou gravar. Ex. Texto, Data, Float
        e etc);

    3.  **Tamanho** (quantos caracteres poderá armazenar esse campo);

    4.  **Predefinido** (um valor já pré-selecionado);

    5.  **Agrupamento** (tipo de caracteres, como a tabela já foi
        definida com um agrupamento esse pode ficar em branco);

    6.  **Atributos** (geralmente não se mexe nesses dados);

    7.  **Nulo** (indica se o campo pode ser nulo ou não);

    8.  **Indice** (indica se o campo será um indice);

    9.  **A\_I** (auto-incremento).

5.  Crie os campos na ordem descrita abaixo:

    1.  Nome: id, Tipo: INT, e marque a opção A\_I;

    2.  Nome: nome, Tipo: Varchar, Tamanho: 200;

    3.  Nome: login, Tipo: Varchar, Tamanho: 20, Índice UNIQUE;

    4.  Nome: senha, Tipo: Varchar, Tamanho: 32;

    5.  Nome: email, Tipo: Varchar, Tamanho: 200, Índice UNIQUE;

6.  No campo “Storage Engine” marque a opção InnoDB.

Vamos agora criar nosso arquivo de conexão com banco de dados.

Conexão
-------

1.  &lt;?php

2.  //Abre uma conexao com o banco de dados

3.  function dbConnect()

4.  {

5.  \$host = 'localhost';

6.  \$user = 'root';

7.  \$pass = 'toor';

8.  \$db = 'curso-php-basico0';

9.  10. \$con = mysqli\_connect(\$host, \$user, \$pass, \$db)

11. or die (mysqli\_connect\_error(\$con));

12. mysqli\_set\_charset(\$con, 'utf8') or die (mysqli\_error());

13. 14. return \$con;

15. }

16. 17. //Fecha a conexao com o banco de dados

18. function dbClose(\$con)

19. {

20. mysqli\_close(\$con);

21. }

22. 

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/conexao.php, no browser
digite*
[http://localhost/PHPBasico/Cap9/](http://localhost/PHPBasico/Cap9/conexao.php)[*conexao*](http://localhost/PHPBasico/Cap9/conexao.php)[*.*](http://localhost/PHPBasico/Cap9/conexao.php)[*php*](http://localhost/PHPBasico/Cap9/conexao.php).

**Nota:** MySQL versão 4.1.3 maior ou igual e PHP versão 5.3 maior ou
igual deve-se sempre usar as funções mysqli.

Vamos ver como era a antiga biblioteca do PHP para o MySQL.

Conexão com a biblioteca antiga
-------------------------------

1.  &lt;?php

2.  //Abre uma conexao com o banco de dados

3.  function dbConnect()

4.  {

5.  \$host = 'localhost';

6.  \$user = 'root';

7.  \$pass = 'toor';

8.  \$db = 'curso-php-basico';

9.  10. \$con = mysql\_connect(\$host, \$user, \$pass)

11. or die (mysql\_error());

12. // Conecta ao banco de dados

13. mysql\_select\_db(\$db) or die (mysql\_error());

14. 15. return \$con;

16. }

17. 18. //Fecha a conexao com o banco de dados

19. function dbClose(\$con)

20. {

21. mysql\_close(\$con);

22. }

23. 24. dbConnect();

25. 

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/conexaoAntiga.php, no
browser digite*
[http://localhost/PHPBasico/Cap9/](http://localhost/PHPBasico/Cap9/conexao.php)[*conexao*](http://localhost/PHPBasico/Cap9/conexao.php)[*Antiga*](http://localhost/PHPBasico/Cap9/conexao.php)[*.*](http://localhost/PHPBasico/Cap9/conexao.php)[*php*](http://localhost/PHPBasico/Cap9/conexao.php).

**Nota:** Observe que teve pequenas mudanças, a mais importante é o
“**i**” que não existe no nome da função a outra é que precisa do
**mysql\_select\_db()** para informar qual banco de dados será usado.
Essa era a forma usada antes das versões 5.3 do PHP.

O CRUD
------

O CRUD é a sigla que representa as quatro operações básicas de um Banco
de Dados. **C**reate, **R**etrieve/**R**ead, **U**pdate e **D**elete.
Faremos agora essas quatro operações em exercícios separados.

### Create (Inserir)

1.  ...

2.  &lt;h1&gt;Inserir usuarios&lt;/h1&gt;

3.  &lt;?php

4.  //importa o arquivo de conexão

5.  require\_once('conexao.php');

6.  7.  //abre a conexao com o banco

8.  \$con = dbConnect();

9.  10. //define as variávels para o insert 1

11. \$nome1 = 'Carlos';

12. \$login1 = 'carlinhos';

13. \$senha1 = sha1('bobmarley');

14. \$email1 = 'carlos.silva.@bol.com.br';

15. 16. \$sql = "INSERT INTO usuarios (nome, login, senha,

17. email) VALUES ('\$nome1', '\$login1', '\$senha1', '\$email1')";

18. 19. if (mysqli\_query(\$con, \$sql)) {

20. echo '&lt;p&gt;Usuário inserido com sucesso.&lt;/p&gt;';

21. } else {

22. echo '&lt;p&gt;Erro: Não foi possível inserir o usuário&lt;/p&gt;';

23. }

24. 25. //define as variávels para o insert 2

26. \$nome2 = 'José Carlos';

27. \$login2 = 'jcbomzao';

28. \$senha2 = sha1('123456789');

29. \$email2 = 'jcb33@ig.com.br';

30. 31. \$sql = mysqli\_prepare(\$con, "INSERT INTO usuarios (nome,
    login, senha,

32. email) VALUES (?, ?, ?, ?)");

33. 34. mysqli\_stmt\_bind\_param(\$sql, 'ssss', \$nome2, \$login2,
    \$senha2, \$email2);

35. 36. \$qry = mysqli\_stmt\_execute(\$sql);

37. mysqli\_stmt\_close(\$sql);

38. 39. if (\$qry) {

40. echo '&lt;p&gt;Usuário inserido com sucesso.&lt;/p&gt;';

41. } else {

42. echo '&lt;p&gt;Erro: Não foi possível inserir o usuário&lt;/p&gt;';

43. }

44. 45. //fecha a conexao

46. dbClose(\$con);

47. ?&gt;

48. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/inserir.php, no browser
digite*
[http://localhost/PHPBasico/Cap9/](http://localhost/PHPBasico/Cap9/inserir.php)[*inserir*](http://localhost/PHPBasico/Cap9/inserir.php)[*.*](http://localhost/PHPBasico/Cap9/inserir.php)[*php*](http://localhost/PHPBasico/Cap9/inserir.php).

### Retrieve/Read (Consultar)

1.  ...

2.  &lt;h1&gt;Consultar usuarios&lt;/h1&gt;

3.  &lt;?php

4.  //importa o arquivo de conexão

5.  require\_once('conexao.php');

6.  7.  //abre a conexao com o banco

8.  \$con = dbConnect();

9.  \$nome = 'Carlos';

10. 11. //consulta simples

12. \$sql1 = "SELECT id, nome, login, senha, email FROM usuarios WHERE
    nome LIKE '%\$nome%'";

13. \$result = mysqli\_query(\$con, \$sql1); //Executa a consulta

14. 15. \$dados1 = mysqli\_fetch\_array(\$result);

16. \$dados2 = mysqli\_fetch\_assoc(\$result);

17. 18. var\_dump(\$dados1);

19. var\_dump(\$dados2);

20. 21. //acessando dados do mysqli\_fetch\_array()

22. echo '&lt;br&gt;Nome: ' . \$dados1\[1\] . ', E-mail: ' .
    \$dados1\['email'\];

23. 24. //acessando dados do mysqli\_fetch\_assoc()

25. echo '&lt;br&gt;Nome: ' . \$dados2\['nome'\] . ', E-mail: ' .
    \$dados2\['email'\];

26. 27. mysqli\_free\_result(\$result);

28. 29. //fecha a conexao

30. dbClose(\$con);

31. ?&gt;

32. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/consultar1.php, no
browser digite*
[http://localhost/PHPBasico/Cap9/](http://localhost/PHPBasico/Cap9/inserir.php)[*consultar1*](http://localhost/PHPBasico/Cap9/inserir.php)[*.*](http://localhost/PHPBasico/Cap9/inserir.php)[*php*](http://localhost/PHPBasico/Cap9/inserir.php).

1.  ...

2.  &lt;h1&gt;Consultar usuarios&lt;/h1&gt;

3.  &lt;h2&gt;Evitando SQL Injection&lt;/h2&gt;

4.  &lt;?php

5.  //importa o arquivo de conexão

6.  require\_once('conexao.php');

7.  8.  //abre a conexao com o banco

9.  \$con = dbConnect();

10. \$nome = '%Carlos%';

11. 12. //consulta preparada contra SQL Injection

13. \$sql = "SELECT id, nome, login, senha, email FROM usuarios WHERE
    nome LIKE ?";

14. \$result = mysqli\_prepare(\$con, \$sql); //Executa a consulta

15. 16. if (\$result) {

17. mysqli\_stmt\_bind\_param(\$result, 's', \$nome);

18. mysqli\_stmt\_execute(\$result);

19. mysqli\_stmt\_bind\_result(\$result, \$id, \$nome, \$login, \$senha,
    \$email);

20. 21. while (mysqli\_stmt\_fetch(\$result)) {

22. echo \$nome . '&lt;br /&gt;';

23. }

24. 25. mysqli\_stmt\_close(\$result);

26. } else {

27. trigger\_error('Statement failed: ' . mysqli\_stmt\_error(\$result),
    E\_USER\_ERROR);

28. }

29. 30. //fecha a conexao

31. dbClose(\$con);

32. ?&gt;

33. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/consultar2.php, no
browser digite*
[http://localhost/PHPBasico/Cap9/](http://localhost/PHPBasico/Cap9/consultar2.php)[*consultar*](http://localhost/PHPBasico/Cap9/consultar2.php)[*2*](http://localhost/PHPBasico/Cap9/consultar2.php)[*.*](http://localhost/PHPBasico/Cap9/consultar2.php)[*php*](http://localhost/PHPBasico/Cap9/consultar2.php).

**Nota:** Nas consultas que dependem de interação com o usuário é
**extremamente** recomendado utilizar os **prepared statmens**. Porem,
se decidir usar a forma convencional é de suma importância utilizar as
funções do PHP para “escapar” caracteres nocivos para a consulta, como
por exemplo a função **mysqli\_escape\_string()**.

### Update (Atualizar)

1.  ...

2.  &lt;h1&gt;Atualizar usuario&lt;/h1&gt;

3.  &lt;?php

4.  //importa o arquivo de conexão

5.  require\_once('conexao.php');

6.  7.  //abre a conexao com o banco

8.  \$con = dbConnect();

9.  10. //consulta simples

11. \$sql = "UPDATE usuarios SET nome = 'Carlos Silva' WHERE id = 13";

12. mysqli\_query(\$con, \$sql);

13. 14. if (mysqli\_affected\_rows(\$con)) {

15. echo '&lt;p&gt;Usuário alterado com sucesso.&lt;/p&gt;';

16. } else {

17. echo '&lt;p&gt;Erro: Não foi possível alterar o usuário&lt;/p&gt;';

18. }

19. 20. //liberira memória

21. mysqli\_free\_result(\$qry);

22. 23. //fecha a conexao

24. dbClose(\$con);

25. ?&gt;

26. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/atualizar1.php, no
browser digite*
[http://localhost/PHPBasico/Cap9/](http://localhost/PHPBasico/Cap9/atualizar1.php)[*atualizar1*](http://localhost/PHPBasico/Cap9/atualizar1.php)[*.*](http://localhost/PHPBasico/Cap9/atualizar1.php)[*php*](http://localhost/PHPBasico/Cap9/atualizar1.php).

1.  ...

2.  &lt;h1&gt;Atualizar usuario&lt;/h1&gt;

3.  &lt;h2&gt;Evitando SQL Injection&lt;/h2&gt;

4.  &lt;?php

5.  //importa o arquivo de conexão

6.  require\_once('conexao.php');

7.  8.  //abre a conexao com o banco

9.  \$con = dbConnect();

10. \$nome = 'Carlos';

11. \$id = 13;

12. 13. //consulta preparada contra SQL Injection

14. \$sql = "UPDATE usuarios SET nome = ? WHERE id = ?";

15. \$result = mysqli\_prepare(\$con, \$sql); //Executa a consulta

16. mysqli\_stmt\_bind\_param(\$result, 'si', \$nome, \$id);

17. mysqli\_stmt\_execute(\$result);

18. 19. if (mysqli\_affected\_rows(\$con)) {

20. echo '&lt;p&gt;Usuário alterado com sucesso.&lt;/p&gt;';

21. } else {

22. echo '&lt;p&gt;Erro: Não foi possível alterar o usuário&lt;/p&gt;';

23. }

24. //liberira memória

25. mysqli\_stmt\_close(\$result);

26. 27. //fecha a conexao

28. dbClose(\$con);

29. ?&gt;

30. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/atualizar2.php, no
browser digite*
[http://localhost/PHPBasico/Cap9/](http://localhost/PHPBasico/Cap9/atualizar2.php)[*atualizar2*](http://localhost/PHPBasico/Cap9/atualizar2.php)[*.*](http://localhost/PHPBasico/Cap9/atualizar2.php)[*php*](http://localhost/PHPBasico/Cap9/atualizar2.php).

### Delete (Deletar)

1.  ...

2.  &lt;h1&gt;Deletar usuario&lt;/h1&gt;

3.  &lt;?php

4.  //importa o arquivo de conexão

5.  require\_once('conexao.php');

6.  7.  //abre a conexao com o banco

8.  \$con = dbConnect();

9.  10. //consulta simples

11. \$sql = "DELETE FROM usuarios WHERE id = 15";

12. mysqli\_query(\$con, \$sql);

13. 14. if (mysqli\_affected\_rows(\$con)) {

15. echo '&lt;p&gt;Usuário deletado com sucesso.&lt;/p&gt;';

16. } else {

17. echo '&lt;p&gt;Erro: Não foi possível deletar o usuário&lt;/p&gt;';

18. }

19. //liberira memória

20. mysqli\_free\_result(\$qry);

21. 22. //fecha a conexao

23. dbClose(\$con);

24. ?&gt;

25. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/deletar1.php, no browser
digite*
[http://localhost/PHPBasico/Cap9/deletar](http://localhost/PHPBasico/Cap9/deletar1.php)[*1*](http://localhost/PHPBasico/Cap9/deletar1.php)[*.*](http://localhost/PHPBasico/Cap9/deletar1.php)[*php*](http://localhost/PHPBasico/Cap9/deletar1.php).

1.  ...

2.  &lt;h1&gt;Deletar usuario&lt;/h1&gt;

3.  &lt;h2&gt;Evitando SQL Injection&lt;/h2&gt;

4.  &lt;?php

5.  //importa o arquivo de conexão

6.  require\_once('conexao.php');

7.  8.  //abre a conexao com o banco

9.  \$con = dbConnect();

10. \$id = 16;

11. 12. //consulta preparada contra SQL Injection

13. \$sql = "DELETE FROM usuarios WHERE id = ?";

14. \$result = mysqli\_prepare(\$con, \$sql); //Executa a consulta

15. mysqli\_stmt\_bind\_param(\$result, 'i', \$id);

16. mysqli\_stmt\_execute(\$result);

17. 18. if (mysqli\_affected\_rows(\$con)) {

19. echo '&lt;p&gt;Usuário deletado com sucesso.&lt;/p&gt;';

20. } else {

21. echo '&lt;p&gt;Erro: Não foi possível deletar o usuário&lt;/p&gt;';

22. }

23. //liberira memória

24. mysqli\_stmt\_close(\$result);

25. 26. //fecha a conexao

27. dbClose(\$con);

28. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap9/deletar2.php, no browser
digite*
[http://localhost/PHPBasico/Cap9/deletar](http://localhost/PHPBasico/Cap9/atualizar1.php)[*2*](http://localhost/PHPBasico/Cap9/atualizar1.php)[*.*](http://localhost/PHPBasico/Cap9/atualizar1.php)[*php*](http://localhost/PHPBasico/Cap9/atualizar1.php).

**Atenção:** Ao executar os comandos **UPDATE** e **DELETE**
certifique-se que esteja usando a cláusula **WHERE**. Pois se não fizer
isso **TODOS** os registros da tabela serão alterados ou deletados.

Resumo do Capítulo
------------------

Nesse capítulo aprendemos como fazer as quatro operações básicas de um
banco de dados, o **CRUD**. Vimos também como dar um pouco mais de
segurança a nossa aplicação com os **prepare statements**.

Exercícios
----------

1.  Crie um script que faça um insert no banco pegando dados do
    formulário usando o prepared statements;

2.  Crie um script que faça um select no banco pegando dados do
    formulário usando o prepared statements;

3.  Crie um script que faça um update no banco pegando dados do
    formulário usando o prepared statements;

4.  Crie um script que faça um delete no banco pegando dados do
    formulário usando o prepared statements;

5.  Crie um CRUD usando a biblioteca PDO do PHP (para fazer esse
    exercício será necessário uma consulta no manual do PHP).
