
Capítulo 5
==========

Nesse capítulo abordaremos como disparar e-mail com o PHP usando a
função mail.

Função Mail
-----------

Essa função é responsável por disparar e-mails usando o PHP. Ela suporta
todas as configurações que são usadas normalmente em um webmail.
Configurações como, anexo, mime-type entre outras.

Abaixo um breve descritivo dos parâmetros da função.

-   **$to (*string*)** – Destinatário (para quem vai a mensagem);

-   **$subject (*string*)** – Assunto;

-   **$message (*string*)** – Mensagem;

-   **$adtional\_headers (*string*)** – Informações do Cabeçalho do
    e-mail (opcional);

-   **$adition\_parameters (*string*)** – Usado para definição
    de sendmail\_paht() (opcional);

### Envio de e-mail simples
```
...
<h1>Envio de e-mail simples</h1>

<?php
    $to = "calcionit@gmail.com";
    $subject = "Testando";
    $message = "Isso é um teste de envio";

    mail($to, $subject, $message);
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email1.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email1.php)[5](http://localhost/PHPBasico/Cap5/email1.php)[/](http://localhost/PHPBasico/Cap5/email1.php)[email1](http://localhost/PHPBasico/Cap5/email1.php)[.](http://localhost/PHPBasico/Cap5/email1.php)[php](http://localhost/PHPBasico/Cap5/email1.php).

### Envio de e-mail usando o header
```
...
<h1>Envio de e-mail usando o header</h1>

<?php
    $to = "calcionit@gmail.com";
    $subject = "Testando";
    $message = "Isso é um teste de envio";

    $headers = 'From: webmaster@site.com.br' . "\\r\\n" .
    'Reply-To: webmaster@site.com.br' . "\\r\\n" .
    'X-Mailer: PHP/' . phpversion();

    mail($to, $subject, $message, $headers);
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email2.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email2.php)[5](http://localhost/PHPBasico/Cap5/email2.php)[/](http://localhost/PHPBasico/Cap5/email2.php)[email2](http://localhost/PHPBasico/Cap5/email2.php)[.](http://localhost/PHPBasico/Cap5/email2.php)[php](http://localhost/PHPBasico/Cap5/email2.php).

### Envio de e-mail em HTML
```
...
<h1>Envio de e-mail em HTML</h1>

<?php
    $to = "calcionit@gmail.com";
    $subject = "Testando";

    $message = "
    <h1>Isso é um teste de envio</h1>
    <p>Aqui pode ir um texto longo, imagens e listas</p>
    <hr />
    <p>Pode incluir qualquer tag HTML e CSS também</p>
    ";

    $headers = 'MIME-Version: 1.0' . "\\r\\n";
    $headers .= 'Content-type:text/html;charset=UTF-8' . "\\r\\n";
    $headers .= 'From: webmaster <webmaster@site.com.br>, alguém
    <alguem@site.com.br' . "\\r\\n";
    $headers .= 'Reply-To: webmaster <webmaster@site.com.br>' .
    "\\r\\n";
    $headers .= 'Cc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";
    $headers .= 'Bcc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";
    $headers .= 'X-Mailer: PHP' . phpversion();

    mail($to, $subject, $message, $headers);
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email3.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email3.php)[5](http://localhost/PHPBasico/Cap5/email3.php)[/](http://localhost/PHPBasico/Cap5/email3.php)[email](http://localhost/PHPBasico/Cap5/email3.php)[3](http://localhost/PHPBasico/Cap5/email3.php)[.](http://localhost/PHPBasico/Cap5/email3.php)[php](http://localhost/PHPBasico/Cap5/email3.php).

### Testando se o e-mail foi enviado
```
...
<h1>Testando se o e-mail foi enviado</h1>

<?php
    $to = "calcionit@gmail.com";
    $subject = "Testando";

    $message = "
    <h1>Isso é um teste de envio</h1>
    <p>Aqui pode ir um texto longo, imagens e listas</p>
    <hr />
    <p>Pode incluir qualquer tag HTML e CSS também</p>
    ";

    $headers = 'MIME-Version: 1.0' . "\\r\\n";
    $headers .= 'Content-type:text/html;charset=UTF-8' . "\\r\\n";
    $headers .= 'From: webmaster <webmaster@site.com.br>, alguém
    <alguem@site.com.br' . "\\r\\n";
    $headers .= 'Reply-To: webmaster <webmaster@site.com.br>' .
    "\\r\\n";
    $headers .= 'Cc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";
    $headers .= 'Bcc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";
    $headers .= 'X-Mailer: PHP' . phpversion();

    if (mail($to, $subject, $message, $headers)) {
        '<strong>E-mail enviado com sucesso!</strong>';
    } else {
        echo '<strong>Erro: Não foi possível enviar o e-mail!</strong>';
    }
?>
...
```

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email4.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email4.php)[5](http://localhost/PHPBasico/Cap5/email4.php)[/](http://localhost/PHPBasico/Cap5/email4.php)[email](http://localhost/PHPBasico/Cap5/email4.php)[4](http://localhost/PHPBasico/Cap5/email4.php)[.](http://localhost/PHPBasico/Cap5/email4.php)[php](http://localhost/PHPBasico/Cap5/email4.php).

Resumo do capítulo
------------------

Nesse capítulo aprendemos como fazer envio de e-mail diretamente com o
PHP. No entanto, para elas funcionarem o seu servidor de hospedagem
precisa estar com as configurações feitas, caso contrário o envio
falhará.
