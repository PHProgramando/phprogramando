
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

-   **\$to (*string*)** – Destinatário (para quem vai a mensagem);

-   **\$subject (*string*)** – Assunto;

-   **\$message (*string*)** – Mensagem;

-   **\$adtional\_headers (*string*)** – Informações do Cabeçalho do
    e-mail (opcional);

-   **\$adition\_parameters (*string*)** – Usado para definição
    de sendmail\_paht() (opcional);

### Envio de e-mail simples

1.  ...

2.  &lt;h1&gt;Envio de e-mail simples&lt;/h1&gt;

3.  &lt;?php

4.  \$to = "calcionit@gmail.com";

5.  \$subject = "Testando";

6.  \$message = "Isso é um teste de envio";

7.  8.  mail(\$to, \$subject, \$message);

9.  ?&gt;

10. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email1.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email1.php)[5](http://localhost/PHPBasico/Cap5/email1.php)[/](http://localhost/PHPBasico/Cap5/email1.php)[email1](http://localhost/PHPBasico/Cap5/email1.php)[.](http://localhost/PHPBasico/Cap5/email1.php)[php](http://localhost/PHPBasico/Cap5/email1.php).

### Envio de e-mail usando o header

1.  ...

2.  &lt;h1&gt;Envio de e-mail usando o header&lt;/h1&gt;

3.  &lt;?php

4.  \$to = "calcionit@gmail.com";

5.  \$subject = "Testando";

6.  \$message = "Isso é um teste de envio";

7.  \$headers = 'From: webmaster@site.com.br' . "\\r\\n" .

8.  'Reply-To: webmaster@site.com.br' . "\\r\\n" .

9.  'X-Mailer: PHP/' . phpversion();

10. 11. mail(\$to, \$subject, \$message, \$headers);

12. ?&gt;

13. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email2.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email2.php)[5](http://localhost/PHPBasico/Cap5/email2.php)[/](http://localhost/PHPBasico/Cap5/email2.php)[email2](http://localhost/PHPBasico/Cap5/email2.php)[.](http://localhost/PHPBasico/Cap5/email2.php)[php](http://localhost/PHPBasico/Cap5/email2.php).

### Envio de e-mail em HTML

1.  ...

2.  &lt;h1&gt;Envio de e-mail em HTML&lt;/h1&gt;

3.  &lt;?php

4.  \$to = "calcionit@gmail.com";

5.  \$subject = "Testando";

6.  7.  \$message = "

8.  &lt;h1&gt;Isso é um teste de envio&lt;/h1&gt;

9.  &lt;p&gt;Aqui pode ir um texto longo, imagens e listas&lt;/p&gt;

10. &lt;hr /&gt;

11. &lt;p&gt;Pode incluir qualquer tag HTML e CSS também&lt;/p&gt;

12. ";

13. 14. \$headers = 'MIME-Version: 1.0' . "\\r\\n";

15. \$headers .= 'Content-type:text/html;charset=UTF-8' . "\\r\\n";

16. \$headers .= 'From: webmaster &lt;webmaster@site.com.br&gt;, alguém
    &lt;alguem@site.com.br' . "\\r\\n";

17. \$headers .= 'Reply-To: webmaster &lt;webmaster@site.com.br&gt;' .
    "\\r\\n";

18. \$headers .= 'Cc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";

19. \$headers .= 'Bcc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";

20. \$headers .= 'X-Mailer: PHP/' . phpversion();

21. 22. mail(\$to, \$subject, \$message, \$headers);

23. ?&gt;

24. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email3.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email3.php)[5](http://localhost/PHPBasico/Cap5/email3.php)[/](http://localhost/PHPBasico/Cap5/email3.php)[email](http://localhost/PHPBasico/Cap5/email3.php)[3](http://localhost/PHPBasico/Cap5/email3.php)[.](http://localhost/PHPBasico/Cap5/email3.php)[php](http://localhost/PHPBasico/Cap5/email3.php).

### Testando se o e-mail foi enviado

1.  ...

2.  &lt;h1&gt;Testando se o e-mail foi enviado&lt;/h1&gt;

3.  &lt;?php

4.  \$to = "calcionit@gmail.com";

5.  \$subject = "Testando";

6.  7.  \$message = "

8.  &lt;h1&gt;Isso é um teste de envio&lt;/h1&gt;

9.  &lt;p&gt;Aqui pode ir um texto longo, imagens e listas&lt;/p&gt;

10. &lt;hr /&gt;

11. &lt;p&gt;Pode incluir qualquer tag HTML e CSS também&lt;/p&gt;

12. ";

13. 14. \$headers = 'MIME-Version: 1.0' . "\\r\\n";

15. \$headers .= 'Content-type:text/html;charset=UTF-8' . "\\r\\n";

16. \$headers .= 'From: webmaster &lt;webmaster@site.com.br&gt;, alguém
    &lt;alguem@site.com.br' . "\\r\\n";

17. \$headers .= 'Reply-To: webmaster &lt;webmaster@site.com.br&gt;' .
    "\\r\\n";

18. \$headers .= 'Cc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";

19. \$headers .= 'Bcc: outromail@site.com.br, maisum@site.com.br' .
    "\\r\\n";

20. \$headers .= 'X-Mailer: PHP/' . phpversion();

21. 22. if (mail(\$to, \$subject, \$message, \$headers)) {

23. echo '&lt;strong&gt;E-mail enviado com sucesso!&lt;/strong&gt;';

24. } else {

25. echo '&lt;strong&gt;Erro: Não foi possível enviar o
    e-mail!&lt;/strong&gt;';

26. }

27. ?&gt;

28. ...

Salve em */home/seu\_usuario/www/PHPBasico/Cap5/email4.php*, no browser
digite
[http://localhost/PHPBasico/Cap](http://localhost/PHPBasico/Cap5/email4.php)[5](http://localhost/PHPBasico/Cap5/email4.php)[/](http://localhost/PHPBasico/Cap5/email4.php)[email](http://localhost/PHPBasico/Cap5/email4.php)[4](http://localhost/PHPBasico/Cap5/email4.php)[.](http://localhost/PHPBasico/Cap5/email4.php)[php](http://localhost/PHPBasico/Cap5/email4.php).

Resumo do capítulo
------------------

Nesse capítulo aprendemos como fazer envio de e-mail diretamente com o
PHP. No entanto, para elas funcionarem o seu servidor de hospedagem
precisa estar com as configurações feitas, caso contrário o envio
falhará.
