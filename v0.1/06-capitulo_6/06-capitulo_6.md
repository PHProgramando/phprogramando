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
PHP do tipo **$_POST[]** e formulário do tipo ***get*** devem ser
recebidos pela variável global **$_GET[]**. Existe um tipo especial
que é o $_REQUEST[], que recebe tanto o tipo *get* quanto o tipo
*post*, porém seu uso deve ser muito restrito (evitado).

**Nota:** Todas as vezes que sua aplicação receber dados de um
formulário ou tiver interação com o usuário esses dados **DEVEM** ser
tratados por meio de algumas funções do PHP.

### Recuperando campos de texto via $_POST[].
```
...
<h1>Formulário simples 1 (POST)</h1>

<form action="<?= $_SERVER['PHP_SELF'] ?>" name="frmSimples1" id="frmSimples1" method="post">
    <input type="hidden" name="opc" value="1"> 

    <label>Nome:</label>
    <input type="text" name="nome" id="nome" maxlength="150"
    size="50">

    <br />
    <label>E-mail:</label>
    <input type="text" name="email" id="email" maxlength="150"
    size="50">

    <br /><br />
    <input type="submit" name="enviar">
</form>

<?php
    if (isset($_POST['opc']) == '1') :

        echo '<h2>Recuperando campos de texto do tipo post</h2>';

        echo 'Nome: ' . $_POST['nome'];
        echo '<br />E-mail: ' . $_POST['email'];
    endif;
?>
...
```

Salve em */home/seu_usuario/www/PHPBasico/Cap6/formSimples1.php*, no
browser digite <http://localhost/PHPBasico/Cap6/formSimples1.php>.

**Nota:** Todos os campos são recuperados da mesma forma, porém campos
do tipo checkbox tem um comportamento um pouco diferente dos outros.

### Recuperando campos de texto via $_GET[].

Salve o arquivo anterior como *formSimples2.php* e altere o ***method***
do formulário para o tipo **get** e substitua ***$_POST*** por
***$_GET***. Digite no browser
[http://localhost/PHPBasico/Cap6/formSimples](http://localhost/PHPBasico/Cap6/formSimples1.php)[2](http://localhost/PHPBasico/Cap6/formSimples1.php)[.php](http://localhost/PHPBasico/Cap6/formSimples1.php).

**Nota:** Uma atenção especial deve ser dada ao se recuperar pelo método
get, esse protocolo só aceita 255 caracteres.

**Obs:** links em modo geral são recuperados também com o
**$_GET[]**.

### Recuperando campos do tipo checkbox e radiobutton.
```
...
<h1>Formulário simples 3</h1>

<form action="<?= $_SERVER['PHP_SELF'] ?>" name="frmSimples3" id="frmSimples3" method="post">
    <input type="hidden" name="opc" value="1">

    <label>Qual seu nível de conhecimento em PHP?<br
    /></label>
    <input type="radio" name='conhecimento' value='Não sei PHP'>
    Não sei PHP <br />

    <input type="radio" name='conhecimento' value='PHP Básico'>
    PHP Básico <br />

    <input type="radio" name='conhecimento' value='PHP
    Intermediário'> PHP Intermediário <br />

    <input type="radio" name='conhecimento' value='PHP Avançado'>
    PHP Avançado <br />

    <input type="radio" name='conhecimento' value='Jedi'> Jedi
    <br /><br />

    <label>Quais versão do PHP já utilizou?<br /></label>
    <input type="checkbox" name='versao[]' value='3.x'> 3.x
    <br />

    <input type="checkbox" name='versao[]' value='4.x'> 4.x
    <br />

    <input type="checkbox" name='versao[]' value='5.0'> 5.0
    <br />

    <input type="checkbox" name='versao[]' value='5.3'> 5.3
    <br />

    <input type="checkbox" name='versao[]' value='5.5'> 5.5
    <br /><br /><br />

    <input type="submit" name="enviar">

</form>

<?php

if (isset($_POST['opc']) == '1') :
    echo '<h2>Recuperando campos Checkbox e Radiobutton</h2>';

    echo 'Qual seu nível de conhecimento em PHP?<br />';
    echo 'R: ' . $_POST['conhecimento'] . '<br /><br />';
    echo 'Quais versão do PHP já utilizou?<br />';
    echo 'R: ' . $_POST['versao'][0] . '<br />'; //recupera o primeiro item selecionado

    var_dump($_POST['versao']); //Recupera todos os itens marcados
endif;
?>
...
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/formSimples3.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/formSimples*](http://localhost/PHPBasico/Cap6/formSimples3.php)[*3*](http://localhost/PHPBasico/Cap6/formSimples3.php)[*.php*](http://localhost/PHPBasico/Cap6/formSimples3.php)*.*

Tratamento de dados recuperados de formulário
---------------------------------------------

É altamente recomendado tratar e validar quais quer dado que venha de um
formulário, isso vai garantir um pouco mais de segurança em seu site.
Abordarei aqui as principais e mais comuns funções de tratamento e
validação. O Exercício a seguir mostrará como aplicar essas validações.

### Tratamento de formulário com trim(), addslashes(), htmlspecialchars() e htmlentities()
```
...
<h1>Tratando form 1</h1>

<form action="<?= $_SERVER['PHP_SELF'] ?>" name="frmTrata1" id="frmTrata1" method="post">
    <input type="hidden" name="opc" value="1">

    <label>Nome:</label>
    <input type="text" name="nome" id="nome" maxlength="150" size="50">

    <br />
    <label>E-mail:</label>

    <input type="text" name="email" id="email" maxlength="150" size="50">

    <br /><br />
    <input type="submit" name="enviar">
</form>

<?php
    if (isset($_POST['opc']) == '1') :
        echo '<h2>Recuperando e tratando campos de texto do tipo post</h2>';
        Nome: ' . addslashes($_POST['nome']);

        echo '<br /><br />Nome: ' . htmlspecialchars(trim($_POST['nome']), ENT_COMPAT); //padrão

        echo '<br />E-mail: ' . htmlspecialchars(trim($_POST['email']), ENT_QUOTES);
        echo '<br /><br />Nome: ' . htmlentities(trim($_POST['nome']));
        echo '<br />E-mail: ' . htmlentities(trim($_POST['email']));
        echo '<br /><br />Nome: ' . htmlspecialchars(addslashes(trim($_POST['nome'])));

        echo '<br />E-mail: ' . htmlentities(addslashes(trim($_POST['email'])));
endif;
?>
...
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/tratandoForm1.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/*](http://localhost/PHPBasico/Cap6/tratandoForm1.php)[*tratandoForm1.php*](http://localhost/PHPBasico/Cap6/tratandoForm1.php)*.*

### *Tratamento de formulário com nl2br()*
```
...

<h1>Tratando form 2</h1>

<form action="<?= $_SERVER['PHP_SELF'] ?>" name="frmTrata2" id="frmTrata2" method="post">

    <label>Nome:</label>
    <input type="text" name="nome" id="nome" maxlength="150" size="50">

    <br />
    <label>E-mail:</label>

    <input type="text" name="email" id="email" maxlength="150" size="50">

    <br />
    <label>Comentário:</label>

    <textarea name="comentario" id="comentario" cols="63" rows="10"></textarea>

    <br /><br />
    <input type="submit" name="enviar">
</form>

<?php
    if ($_POST) :
        echo '<br /><br />Nome: ' . htmlspecialchars(addslashes(trim($_POST['nome'])));
        echo '<br />E-mail: ' . htmlentities(addslashes(trim($_POST['email'])));
        echo '<br /><br />Nome: ' . addslashes(nl2br(trim($_POST['comentario'])));
    endif;
?>
...
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/tratandoForm2.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)[*tratandoForm*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)[*2*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)[*.php*](http://localhost/PHPBasico/Cap6/tratandoForm2.php)*.*

Envio (upload) de arquivo
-------------------------

O upload de arquivos é muito comum em um site. Mas para que ele funcione
seu formulário precisa informar ao HTML que ele será ser usado com a
finalidade de upload, para isso basta utilizar o atributo
*enctype="multipart/form-data"* na tag form.

### Envio de dados com PHP e validação
```
...
<h1>Upload de arquivo e validação</h1>

<form action="<?= $_SERVER['PHP_SELF'] ?>" name="frmUpload" id="frmUpload" method="post" enctype="multipart/form-data">

    <label>Selecione uma magem:<br /></label>
    <input type="file" name="img" id="img" accept="image/\*">

    <br /><br />
    <label>Selecione um Documento:<br /></label>
    <input type="file" name="doc" id="doc">

    <br /><br />
    <input type="submit" name="enviar">
</form>

<?php
    if ($_POST) :
        var_dump($_FILES['img']);
        var_dump($_FILES['doc']);

        function validaNomeCampo($nomeCampo = null)
        {
            if ($nomeCampo) {
                return true;
            } else {
                echo '<strong>Erro: O nome do campo deve ser informado!</strong>';
                exit;
            }
        }

        function verificaCampoVazio($nomeCampo = nul, array $campo = null)
        {
            if ($_FILES[$nomeCampo]['size'] !== 0) {
                return true;
            } else {
                echo '<strong> - Nenhum arquivo <em>'. $nomeCampo .'</em> para ser enviado!<br /></strong>';
            }
        }

        function validaCampo(array $campo = null)
        {
            if (is_array($campo)) {
                return true;
            } else {
                echo '<strong>Erro: O Campo deve ser um array!</strong>';
                exit;
            }

            if ($campo) {
                return true;
            } else {
                echo '<strong>Erro: O Campo deve ser informado!</strong>';
                exit;
            }
        }

        function upload($nomeCampo = null, array $campo = null)
        {

            $dir = __DIR__ . '/upload/';

            if (validaNomeCampo($nomeCampo)) {
                if (validaCampo($campo)) {
                    $arquivo = $uploadfile = $dir . basename($_FILES[$nomeCampo]['name']);

                    if(move_uploaded_file($_FILES[$nomeCampo]['tmp_name'], $uploadfile))
                    {
                        echo "Arquivo válido e enviado com sucesso.<br />\n";
                    } else {
                        echo "Não foi possível gravar oarquivo<br />\n";
                    }
                }
            }
        }

        if (verificaCampoVazio('img', $_FILES['img'])) {            
            //verificando se upload é uma imagem
            if (!empty($_FILES['img']) && ($_FILES['img']['type'] == 'image/jpeg' ||
            $_FILES['img']['type'] == 'image/jpg' ||
            $_FILES['img']['type'] == 'image/png' ||
            $_FILES['img']['type'] == 'image/gif')) :

                echo 'Grava a imagem no servidor ou banco. Para isso é necessário utilizar $_FILES["img"]["tmp_name"] e ter permissão de escrita no servidor.<br /><br />';

                upload('img', $_FILES['img']);
            else :
                echo 'Erro: Arquivo enviado não é uma imagem.<br /><br/>';
            endif;
        }

        if (verificaCampoVazio('doc', $_FILES['doc'])) {
            //verificando se upload é um documento ou planílha ODF ou PDF
            if ($_FILES['doc']['type'] == 'application/vnd.oasis.opendocument.spreadsheet' ||
            $_FILES['doc']['type'] == 'application/vnd.oasis.opendocument.text' ||
            $_FILES['doc']['type'] == 'application/pdf') :
                echo 'Grava a imagem no servidor ou banco. Para isso é necessário utilizar $_FILES["doc"]["tmp_name"] e ter permissão de escrita no servidor.<br /><br />';

                upload('doc', $_FILES['doc']);
            else :
                'Erro: Arquivo enviado não documento ou planílha ODF ou PDF.<br /><br />';
            endif;
        }
    endif;
?>
...
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/formUpload.php, no
browser digite*
[*http://localhost/PHPBasico/Cap6/*](http://localhost/PHPBasico/Cap6/formUpload.php)[*formUpload*](http://localhost/PHPBasico/Cap6/formUpload.php)[*.php*](http://localhost/PHPBasico/Cap6/formUpload.php)*.*

Evitando o CSRF (Cross Site Request Forgery)
--------------------------------------------

Como já foi falado várias vezes durante o curso, segurança é um ponto
que devemos sempre estar atento. Nesse tópico abordaremos mais ponto de
segurança, o **CSRF**, popularmente conhecido como token de formulário.
Para facilitar o entendimento e testes, faremos os exercícios em várias
etapas e dividiremos em 2 arquivos.
```
...
<h1>Evitando o CSRF (Cross Site Request Forgery)</h1>

<form action="recebeDados.php" name="frmCSRF" id="frmCSRF" method="post">
    
    <label>Nome:</label>
    <input type="text" name="nome" id="nome" maxlength="150" size="50">

    <br />
    <label>E-mail:</label>
    <input type="email" name="email" id="email" maxlength="150" size="50">

    <br />
    <label>Comentário:</label>
    <textarea name="comentario" id="comentario" cols="63" rows="10"></textarea>

    <br /><br />
    <input type="submit" name="enviar">
</form>
...
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php, no
browser digite*
[http://localhost/PHPBasico/Cap6/](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*formEvitandoCSRF*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)[*.php*](http://localhost/PHPBasico/Cap6/formEvitandoCSRF.php)*.*

Continuando a edição do arquivo criado anteriormente. Nesse momento
faremos as principais validações e recuperação dos dados enviados pelo
formulário no PHP. Abra o arquivo
*home/seu_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php* e edite logo
abaixo da tag **<body>**.
```
...
<body>
<?php
    //inicializando variáveis do form
    $nome = $email = $comentario = null;
    $erros = [];

    function exibeErros($campo = null, array $erros = null)
    {
        if (isset($erros[$campo])) {
            echo $erros[$campo];
            unset($erros[$campo]);
        }
    }

    //verifica se houve subimit
    if ($_POST) {
        extract($_POST);

        if (trim($nome) == "") {
            $erros['nome'] = '<br/><div><strong>Erro:</strong> O Campo <strong>nome</strong> deve ser preenchido.</div>';
        }

        if (trim($email) == "") {
            $erros['email'] = '<br /><div><strong>Erro:</strong> O Campo <strong>e-mail</strong> deve ser preenchido.</div>';
        }

        if (trim($comentario) == "") {
            $erros['comentario'] = '<br /><div><strong>Erro:</strong> O Campo <strong>comentário</strong> deve ser preenchido.</div>';
        }

        //Se não houver erro exibe os dados na tela
        if (empty($erros)) {
            echo 'Nome: ' . addslashes(trim($nome)) . '<br />';
            echo 'E-mail: ' . addslashes(trim($email)) . '<br />';
            echo 'Comentário:<br /><br />' . addslashes(trim(nl2br($comentario))) . '<br />';
        }
    }
?>

<h1>Evitando o CSRF (Cross Site Request Forgery)</h1>
...
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php, no
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
```
<?php
    function geraToken()
    {
        return $_SESSION['token'] = base64_encode(openssl_random_pseudo_bytes(32));
    }

    function verificaToken($token)
    {
        if (isset($_SESSION['token']) && $token === $_SESSION['token']) {
            unset($_SESSION['token']);
            return true;
        }

        return false;
    }

//essa linha vazia tem que existir.
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/*protecaoContraCSRF.php.

Continuando a edição do arquivo *formEvitandoCSRF.php*. Nesse momento
faremos a validação necessária para que a proteção contra o CSRF
funcione. Abra o arquivo
*home/seu_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php* e edite o
arquivo logo na primeira linha.
```
<?php
    session_start();
    require_once 'protecaoContraCSRF.php';
?>
```
*Salve em /home/seu_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php.*

*Continue editando o arquivo formEvitandoCSRF.php*. Posicione o cursor
depois do comentário '*if ($_POST) {*', e envolva todo o código PHP
com a validação contra o CSRF, como no exercício abaixo.
```
...
//verifica se houve subimit
if ($_POST) {
    if (verificaToken(isset($_POST['token']))) {
        extract($_POST);

        if (trim($nome) == "") {
            ...

    } //fim do if (verificaToken())
    
    ...

}// fim do if ($_POST)
?>
...
```
*Salve em /home/seu_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php*.

Agora para finalizar, crie um campo do tipo hidden com o nome token.
Esse campo pode ser o primeiro campo do formulário.
```
...
<h1>Evitando o CSRF (Cross Site Request Forgery)</h1>

<form action="" name="frmCSRF" id="frmCSRF" method="post">
    <input type="hidden" name="token" value="<?= geraToken() ?>" />

    <label>Nome:</label>
    ...
```

*Salve em /home/seu_usuario/www/PHPBasico/Cap6/formEvitandoCSRF.php, no
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
