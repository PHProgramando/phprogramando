
Capítulo 6
==========

Nesse capítulo você aprenderá como recuperar dados de formulários, seus
tipos (POST, GET e REQUEST) e formulários que suportam envio de
arquivos.

Recuperando dados de Formulários
--------------------------------

Para recuperar dados vindo de um fomulário é preciso saber qual tipo de
protocolo foi informado no formulário. Para formulário do tipo
***post*** as informações devem ser recebidas pela variável global de
PHP do tipo **\$\_POST\[\]** e formulário do tipo ***get*** devem ser
recebidos pela variável global **\$\_GET\[\]**. Existe um tipo especial
que é o \$\_REQUEST\[\], que recebe tanto o tipo *get* quanto o tipo
*post*, porém seu uso deve ser muito restrito (evitado).

**Nota:** Todas as vezes que sua aplicação receber dados de um
formulário ou tiver interação com o usuário esses dados **DEVEM** ser
tratados por meio de algumas funções do PHP.

### Recuperando campos de texto via \$\_POST\[\].

1.  ..

2.  &lt;h1&gt;Formulário simples 1 (POST)&lt;/h1&gt;

3.  4.  &lt;form action="&lt;?= \$\_SERVER\['PHP\_SELF'\] ?&gt;"

5.  name="frmSimples1" id="frmSimples1" method="post"&gt;

6.  &lt;input type="hidden" name="opc" value="1"&gt;

7.  8.  &lt;label&gt;Nome:&lt;/label&gt;

9.  &lt;input type="text" name="nome" id="nome" maxlength="150"
    size="50"&gt;

10. 11. &lt;br /&gt;

12. &lt;label&gt;E-mail:&lt;/label&gt;

13. &lt;input type="text" name="email" id="email" maxlength="150"
    size="50"&gt;

14. 15. &lt;br /&gt;&lt;br /&gt;

16. &lt;input type="submit" name="enviar"&gt;

17. &lt;/form&gt;

18. 19. &lt;?php

20. if (isset(\$\_POST\['opc'\]) == '1') :

21. echo '&lt;h2&gt;Recuperando campos de texto do tipo
    post&lt;/h2&gt;';

22. 23. echo 'Nome: ' . \$\_POST\['nome'\];

24. echo '&lt;br /&gt;E-mail: ' . \$\_POST\['email'\];

25. endif;

26. ?&gt;

27. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap6/formSimples1.php*, no
browser digite <http://localhost/PHPBasico/Cap6/formSimples1.php>.

**Nota:** Todos os campos são recuperados da mesma forma, porém campos
do tipo checkbox tem um comportamento um pouco diferente dos outros.

### Recuperando campos de texto via \$\_GET\[\].

Salve o arquivo anterior como *formSimples2.php* e altere o ***method***
do formulário para o tipo **get** e substitua ***\$\_POST*** por
***\$\_GET***. Digite no browser
[http://localhost/PHPBasico/Cap6/formSimples](http://localhost/PHPBasico/Cap6/formSimples1.php)[2](http://localhost/PHPBasico/Cap6/formSimples1.php)[.php](http://localhost/PHPBasico/Cap6/formSimples1.php).

**Nota:** Uma atenção especial deve ser dada ao se recuperar pelo método
get, esse protocolo só aceita 255 caracteres.

**Obs:** links em modo geral são recuperados também com o
**\$\_GET\[\]**.

### Recuperando campos do tipo checkbox e radiobutton.

1.  ...

2.  &lt;h1&gt;Formulário simples 3&lt;/h1&gt;

3.  4.  &lt;form action="&lt;?= \$\_SERVER\['PHP\_SELF'\] ?&gt;"

5.  name="frmSimples3" id="frmSimples3" method="post"&gt;

6.  &lt;input type="hidden" name="opc" value="1"&gt;

7.  8.  &lt;label&gt;Qual seu nível de conhecimento em PHP?&lt;br
    /&gt;&lt;/label&gt;

9.  &lt;input type="radio" name='conhecimento' value='Não sei PHP'&gt;
    Não sei PHP &lt;br /&gt;

10. &lt;input type="radio" name='conhecimento' value='PHP Básico'&gt;
    PHP Básico &lt;br /&gt;

11. &lt;input type="radio" name='conhecimento' value='PHP
    Intermediário'&gt; PHP Intermediário &lt;br /&gt;

12. &lt;input type="radio" name='conhecimento' value='PHP Avançado'&gt;
    PHP Avançado &lt;br /&gt;

13. &lt;input type="radio" name='conhecimento' value='Jedi'&gt; Jedi
    &lt;br /&gt;

14. 15. &lt;br /&gt;

16. &lt;label&gt;Quais versão do PHP já utilizou?&lt;br
    /&gt;&lt;/label&gt;

17. &lt;input type="checkbox" name='versao\[\]' value='3.x'&gt; 3.x
    &lt;br /&gt;

18. &lt;input type="checkbox" name='versao\[\]' value='4.x'&gt; 4.x
    &lt;br /&gt;

19. &lt;input type="checkbox" name='versao\[\]' value='5.0'&gt; 5.0
    &lt;br /&gt;

20. &lt;input type="checkbox" name='versao\[\]' value='5.3'&gt; 5.3
    &lt;br /&gt;

21. &lt;input type="checkbox" name='versao\[\]' value='5.5'&gt; 5.5
    &lt;br /&gt;

22. 23. &lt;br /&gt;&lt;br /&gt;

24. &lt;input type="submit" name="enviar"&gt;

25. &lt;/form&gt;

26. 27. &lt;?php

28. if (isset(\$\_POST\['opc'\]) == '1') :

29. echo '&lt;h2&gt;Recuperando campos Checkbox e
    Radiobutton&lt;/h2&gt;';

30. 31. echo 'Qual seu nível de conhecimento em PHP?&lt;br /&gt;';

32. echo 'R: ' . \$\_POST\['conhecimento'\] . '&lt;br /&gt;&lt;br
    /&gt;';

33. 34. echo 'Quais versão do PHP já utilizou?&lt;br /&gt;';

35. echo 'R: ' . \$\_POST\['versao'\]\[0\] . '&lt;br /&gt;'; //recupera
    o primeiro item selecionado

36. var\_dump(\$\_POST\['versao'\]); //Recupera todos os itens marcados

37. endif;

38. ?&gt;

39. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/formSimples3.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/formSimples*](http://localhost/PHPBasico/Cap6/formSimples3.php)[*3*](http://localhost/PHPBasico/Cap6/formSimples3.php)[*.php*](http://localhost/PHPBasico/Cap6/formSimples3.php)*.*

Tratamento de dados recuperados de formulário
---------------------------------------------

É altamente recomendado tratar e validar quais quer dado que venha de um
formulário, isso vai garantir um pouco mais de segurança em seu site.
Abordarei aqui as principais e mais comuns funções de tratamento e
validação. O Exercício a seguir mostrará como aplicar essas validações.

### Tratamento de formulário com trim(), addslashes(), htmlspecialchars() e htmlentities()

1.  ...

2.  &lt;h1&gt;Tratando form 1&lt;/h1&gt;

3.  4.  &lt;form action="&lt;?= \$\_SERVER\['PHP\_SELF'\] ?&gt;"

5.  name="frmTrata1" id="frmTrata1" method="post"&gt;

6.  &lt;input type="hidden" name="opc" value="1"&gt;

7.  8.  &lt;label&gt;Nome:&lt;/label&gt;

9.  &lt;input type="text" name="nome" id="nome" maxlength="150"
    size="50"&gt;

10. 11. &lt;br /&gt;

12. &lt;label&gt;E-mail:&lt;/label&gt;

13. &lt;input type="text" name="email" id="email" maxlength="150"
    size="50"&gt;

14. 15. &lt;br /&gt;&lt;br /&gt;

16. &lt;input type="submit" name="enviar"&gt;

17. &lt;/form&gt;

18. 19. &lt;?php

20. if (isset(\$\_POST\['opc'\]) == '1') :

21. echo '&lt;h2&gt;Recuperando e tratando campos de texto do tipo
    post&lt;/h2&gt;';

22. echo 'Nome: ' . addslashes(\$\_POST\['nome'\]);

23. echo '&lt;br /&gt;&lt;br /&gt;Nome: ' .
    htmlspecialchars(trim(\$\_POST\['nome'\]), ENT\_COMPAT); //padrão

24. echo '&lt;br /&gt;E-mail: ' .
    htmlspecialchars(trim(\$\_POST\['email'\]), ENT\_QUOTES);

25. echo '&lt;br /&gt;&lt;br /&gt;Nome: ' .
    htmlentities(trim(\$\_POST\['nome'\]));

26. echo '&lt;br /&gt;E-mail: ' .
    htmlentities(trim(\$\_POST\['email'\]));

27. echo '&lt;br /&gt;&lt;br /&gt;Nome: ' .
    htmlspecialchars(addslashes(trim(\$\_POST\['nome'\])));

28. echo '&lt;br /&gt;E-mail: ' .
    htmlentities(addslashes(trim(\$\_POST\['email'\])));

29. endif;

30. ?&gt;

31. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/tratandoForm1.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/*](http://localhost/PHPBasico/Cap6/tratandoForm1.php)[*tratandoForm1.php*](http://localhost/PHPBasico/Cap6/tratandoForm1.php)*.*

### *Tratamento de formulário com nl2br()*

1.  ...

2.  &lt;h1&gt;Tratando form 2&lt;/h1&gt;

3.  4.  &lt;form action="&lt;?= \$\_SERVER\['PHP\_SELF'\] ?&gt;"

5.  name="frmTrata2" id="frmTrata2" method="post"&gt;

6.  7.  &lt;label&gt;Nome:&lt;/label&gt;

8.  &lt;input type="text" name="nome" id="nome" maxlength="150"
    size="50"&gt;

9.  10. &lt;br /&gt;

11. &lt;label&gt;E-mail:&lt;/label&gt;

12. &lt;input type="text" name="email" id="email" maxlength="150"
    size="50"&gt;

13. 14. &lt;br /&gt;

15. &lt;label&gt;Comentário:&lt;/label&gt;

16. &lt;textarea name="comentario" id="comentario" cols="63"
    rows="10"&gt;&lt;/textarea&gt;

17. 18. &lt;br /&gt;&lt;br /&gt;

19. &lt;input type="submit" name="enviar"&gt;

20. &lt;/form&gt;

21. 22. &lt;?php

23. if (\$\_POST) :

24. echo '&lt;br /&gt;&lt;br /&gt;Nome: ' .
    htmlspecialchars(addslashes(trim(\$\_POST\['nome'\])));

25. echo '&lt;br /&gt;E-mail: ' .
    htmlentities(addslashes(trim(\$\_POST\['email'\])));

26. echo '&lt;br /&gt;&lt;br /&gt;Nome: ' .
    addslashes(nl2br(trim(\$\_POST\['comentario'\])));

27. endif;

28. ?&gt;

29. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/tratandoForm2.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)[*tratandoForm*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)[*2*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)[*.php*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)*.*

Envio (upload) de arquivo
-------------------------

O upload de arquivos é muito comum em um site. Mas para que ele funcione
seu formulário precisa informar ao HTML que ele será ser usado com a
finalidade de upload, para isso basta utilizar o atributo
*enctype="multipart/form-data"* na tag form.

### Envio de dados com PHP e validação

1.  ...

2.  &lt;h1&gt;Upload de arquivo e validação&lt;/h1&gt;

3.  4.  &lt;form action="&lt;?= \$\_SERVER\['PHP\_SELF'\] ?&gt;"

5.  name="frmUpload" id="frmUpload" method="post"
    enctype="multipart/form-data"&gt;

6.  7.  &lt;label&gt;Selecione uma magem:&lt;br /&gt;&lt;/label&gt;

8.  &lt;input type="file" name="img" id="img" accept="image/\*"&gt;

9.  10. &lt;br /&gt;&lt;br /&gt;

11. &lt;label&gt;Selecione um Documento:&lt;br /&gt;&lt;/label&gt;

12. &lt;input type="file" name="doc" id="doc"&gt;

13. 14. &lt;br /&gt;&lt;br /&gt;

15. &lt;input type="submit" name="enviar"&gt;

16. &lt;/form&gt;

17. 18. &lt;?php

19. 20. if (\$\_POST) :

21. var\_dump(\$\_FILES\['img'\]);

22. var\_dump(\$\_FILES\['doc'\]);

23. 24. function validaNomeCampo(\$nomeCampo = null)

25. {

26. if (\$nomeCampo) {

27. return true;

28. } else {

29. echo '&lt;strong&gt;Erro: O nome do campo deve ser
    informado!&lt;/strong&gt;';

30. exit;

31. }

32. 33. }

34. 35. function verificaCampoVazio(\$nomeCampo = nul, array \$campo
    = null)

36. {

37. if (\$\_FILES\[\$nomeCampo\]\['size'\] !== 0) {

38. return true;

39. } else {

40. echo '&lt;strong&gt; - Nenhum arquivo &lt;em&gt;'. \$nomeCampo
    .'&lt;/em&gt; para ser enviado!&lt;br /&gt;&lt;/strong&gt;';

41. }

42. 43. }

44. 45. function validaCampo(array \$campo = null)

46. {

47. if (is\_array(\$campo)) {

48. return true;

49. } else {

50. echo '&lt;strong&gt;Erro: O Campo deve ser um
    array!&lt;/strong&gt;';

51. exit;

52. }

53. 54. if (\$campo) {

55. return true;

56. } else {

57. echo '&lt;strong&gt;Erro: O Campo deve ser
    informado!&lt;/strong&gt;';

58. exit;

59. }

60. }

61. 62. function upload(\$nomeCampo = null, array \$campo = null)

63. {

64. \$dir = \_\_DIR\_\_ . '/upload/';

65. 66. if (validaNomeCampo(\$nomeCampo)) {

67. if (validaCampo(\$campo)) {

68. \$arquivo = \$uploadfile = \$dir .
    basename(\$\_FILES\[\$nomeCampo\]\['name'\]);

69. 70. if
    (move\_uploaded\_file(\$\_FILES\[\$nomeCampo\]\['tmp\_name'\], \$uploadfile))
    {

71. echo "Arquivo válido e enviado com sucesso.&lt;br /&gt;\\n";

72. } else {

73. echo "Não foi possível gravar oarquivo&lt;br /&gt;\\n";

74. }

75. }

76. }

77. }

78. 79. if (verificaCampoVazio('img', \$\_FILES\['img'\])) {

80. //verificando se upload é uma imagem

81. if (!empty(\$\_FILES\['img'\]) && (\$\_FILES\['img'\]\['type'\] ==
    'image/jpeg' ||

82. \$\_FILES\['img'\]\['type'\] == 'image/jpg' ||

83. \$\_FILES\['img'\]\['type'\] == 'image/png' ||

84. \$\_FILES\['img'\]\['type'\] == 'image/gif')) :

85. echo 'Grava a imagem no servidor ou banco. Para isso é necessário

86. utilizar \$\_FILES\["img"\]\["tmp\_name"\] e ter permissão de
    escrita no

87. servidor.&lt;br /&gt;&lt;br /&gt;';

88. 89. upload('img', \$\_FILES\['img'\]);

90. 91. else :

92. echo 'Erro: Arquivo enviado não é uma imagem.&lt;br /&gt;&lt;br
    /&gt;';

93. endif;

94. }

95. 96. if (verificaCampoVazio('doc', \$\_FILES\['doc'\])) {

97. //verificando se upload é um documento ou planílha ODF ou PDF

98. if (\$\_FILES\['doc'\]\['type'\] ==
    'application/vnd.oasis.opendocument.spreadsheet' ||

99. \$\_FILES\['doc'\]\['type'\] ==
    'application/vnd.oasis.opendocument.text' ||

100. \$\_FILES\['doc'\]\['type'\] == 'application/pdf') :

101. echo 'Grava a imagem no servidor ou banco. Para isso é necessário

102. utilizar \$\_FILES\["doc"\]\["tmp\_name"\] e ter permissão de
    escrita no

103. servidor.&lt;br /&gt;&lt;br /&gt;';

104. 105. upload('doc', \$\_FILES\['doc'\]);

106. 107. else :

108. echo 'Erro: Arquivo enviado não documento ou planílha ODF ou
    PDF.&lt;br /&gt;&lt;br /&gt;';

109. endif;

110. }

111. 112. endif;

113. ?&gt;

114. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/formUpload.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/*](http://localhost/PHPBasico/Cap6/formUpload.php)[*formUpload*](http://localhost/PHPBasico/Cap6/formUpload.php)[*.php*](http://localhost/PHPBasico/Cap6/formUpload.php)*.*

Evitando o CSRF (Cross Site Request Forgery)
--------------------------------------------

Como já foi falado várias vezes durante o curso, segurança é um ponto
que devemos sempre estar atento. Nesse tópico abordaremos mais ponto de
segurança, o **CSRF**, popularmente conhecido como token de formulário.
Para facilitar o entendimento e testes, faremos os exercícios em várias
etapas e dividiremos em 2 arquivos.

1.  ...

2.  &lt;h1&gt;Evitando o CSRF (Cross Site Request Forgery)&lt;/h1&gt;

3.  4.  &lt;form action="recebeDados.php"

5.  name="frmCSRF" id="frmCSRF" method="post"&gt;

6.  7.  &lt;label&gt;Nome:&lt;/label&gt;

8.  &lt;input type="text" name="nome" id="nome" maxlength="150"
    size="50"&gt;

9.  10. &lt;br /&gt;

11. &lt;label&gt;E-mail:&lt;/label&gt;

12. &lt;input type="email" name="email" id="email" maxlength="150"
    size="50"&gt;

13. 14. &lt;br /&gt;

15. &lt;label&gt;Comentário:&lt;/label&gt;

16. &lt;textarea name="comentario" id="comentario" cols="63"
    rows="10"&gt;&lt;/textarea&gt;

17. 18. &lt;br /&gt;&lt;br /&gt;

19. &lt;input type="submit" name="enviar"&gt;

20. &lt;/form&gt;

21. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php, no
browser digite*
[http://localhost/PHPBasico/Cap6/](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*formEvitandoCSRF*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*.php*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)*.*

Continuando a edição do arquivo criado anteriormente. Nesse momento
faremos as principais validações e recuperação dos dados enviados pelo
formulário no PHP. Abra o arquivo
*home/seu\_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php* e edite logo
abaixo da tag **&lt;body&gt;**.

1.  ...

2.  &lt;body&gt;

3.  &lt;?php

4.  //inicializando variáveis do form

5.  \$nome = \$email = \$comentario = null;

6.  \$erros = \[\];

7.  8.  function exibeErros(\$campo = null, array \$erros = null)

9.  {

10. if (isset(\$erros\[\$campo\])) {

11. echo \$erros\[\$campo\];

12. unset(\$erros\[\$campo\]);

13. }

14. }

15. //verifica se houve subimit

16. if (\$\_POST) {

17. extract(\$\_POST);

18. 19. if (trim(\$nome) == "") {

20. \$erros\['nome'\] = '&lt;br
    /&gt;&lt;div&gt;&lt;strong&gt;Erro:&lt;/strong&gt; O Campo
    &lt;strong&gt;nome&lt;/strong&gt; deve ser preenchido.&lt;/div&gt;';

21. }

22. 23. if (trim(\$email) == "") {

24. \$erros\['email'\] = '&lt;br
    /&gt;&lt;div&gt;&lt;strong&gt;Erro:&lt;/strong&gt; O Campo
    &lt;strong&gt;e-mail&lt;/strong&gt; deve ser
    preenchido.&lt;/div&gt;';

25. }

26. 27. if (trim(\$comentario) == "") {

28. \$erros\['comentario'\] = '&lt;br
    /&gt;&lt;div&gt;&lt;strong&gt;Erro:&lt;/strong&gt; O Campo
    &lt;strong&gt;comentário&lt;/strong&gt; deve ser
    preenchido.&lt;/div&gt;';

29. }

30. 31. //Se não houver erro exibe os dados na tela

32. if (empty(\$erros)) {

33. echo 'Nome: ' . addslashes(trim(\$nome)) . '&lt;br /&gt;';

34. echo 'E-mail: ' . addslashes(trim(\$email)) . '&lt;br /&gt;';

35. echo 'Comentário:&lt;br /&gt;&lt;br /&gt;' .
    addslashes(trim(nl2br(\$comentario))) . '&lt;br /&gt;';

36. }

37. }

38. ?&gt;

39. &lt;h1&gt;Evitando o CSRF (Cross Site Request Forgery)&lt;/h1&gt;

40. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php, no
browser digite*
[http://localhost/PHPBasico/Cap6/](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*formEvitandoCSRF*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*.php*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)*.*

Vamos agora testar nosso formulário e veremos como ainda está vulnerável
a ataques. Abra o terminal (CTRL+T) e digite o seguinte comando: ***curl
-d 'nome=qualquer nome&email=qualquer email&comentario=qualquer
comentário'***
<http://localhost/CursoPHP/PHPBasico/Cap6/formEvitandoCSRF.php> e veja
que os valores digitados foram enviados e exibidos na tela. Isso indica
o quão vulnerável ainda está seu formulário.

Dando continuidade ao exercício proposto criaremos um arquivo para fazer
as funções de validações contra o CSRF.

1.  &lt;?php

2.  3.  function geraToken()

4.  {

5.  return \$\_SESSION\['token'\] =
    base64\_encode(openssl\_random\_pseudo\_bytes(32));

6.  }

7.  8.  function verificaToken(\$token)

9.  {

10. if (isset(\$\_SESSION\['token'\]) && \$token
    === \$\_SESSION\['token'\]) {

11. unset(\$\_SESSION\['token'\]);

12. return true;

13. }

14. 15. return false;

16. }

17. //essa linha vazia tem que existir.

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/*protecaoContraCSRF.php.

Continuando a edição do arquivo *ormEvitandoCSRF.php*. Nesse momento
faremos a validação necessária para que a proteção contra o CSRF
funcione. Abra o arquivo
*home/seu\_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php* e edite o
arquivo logo na primeira linha.

1.  &lt;?php

2.  session\_start();

3.  require\_once 'protecaoContraCSRF.php';

4.  ?&gt;

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php.*

*Continue editando o arquivo formEvitandoCSRF.php*. Posicione o cursor
depois do comentário '*if (\$\_POST) {*', e envolva todo o código PHP
com a validação contra o CSRF, como no exercício abaixo.

1.  ...

2.  //verifica se houve subimit

3.  if (\$\_POST) {

4.  if (verificaToken(isset(\$\_POST\['token'\]))) {

5.  extract(\$\_POST);

6.  7.  if (trim(\$nome) == "") {

8.  ...

9.  }// fim do if (verificaToken())

10. ...

11. }// fim do if (\$\_POST)

12. ?&gt;

13. ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php*.

Agora para finalizar, crie um campo do tipo hidden com o nome token.
Esse campo pode ser o primeiro campo do formulário.

1.  ...

2.  &lt;h1&gt;Evitando o CSRF (Cross Site Request Forgery)&lt;/h1&gt;

3.  4.  &lt;form action="" name="frmCSRF" id="frmCSRF" method="post"&gt;

5.  &lt;input type="hidden" name="token" value="&lt;?= geraToken()
    ?&gt;" /&gt;

6.  7.  &lt;label&gt;Nome:&lt;/label&gt;

8.  ...

*Salve em /home/seu\_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php, no
browser digite*
[http://localhost/PHPBasico/Cap6/](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*formEvitandoCSRF*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*.php*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)*.*

Vamos agora testar nosso formulário novamente. Abra o terminal (CTRL+T)
e digite o seguinte comando: ***curl -d 'nome=qualquer
nome&email=qualquer email&comentario=qualquer comentário'***
<http://localhost/CursoPHP/PHPBasico/Cap6/formEvitandoCSRF.php> e veja
que os valores digitados não são exibidos na tela. Isso indica que se
alguém tentar enviar dados sem ser pelo site não conseguirá.

Resumo do Capítulo
------------------

Nesse capítulo aprendemos como recuperar dados passados através de
formulários pelos métodos **POST** e **GET**, como recuperar dados de
campos checkbox, tratamento e validações dos dados recebidos, upload de
arquivos e como tonar seus formulários mais seguros contra o **CSRF**.

Exercícios
----------

1.  Crie um formulário de cadastro básico de cliente contendo os campos:
    Nome, Sobrenome, data de nascimento, senha e-mail e cpf;

2.  Faça as validações necessárias para aplicar a segurança e evitar o
    CSRF;

3.  Se as validações tiverem certas, exibir os dados na tela para
    o usuário.
