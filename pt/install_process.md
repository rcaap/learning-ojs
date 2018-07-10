# Processo de Instalação

Existe um número de componentes a instalar para obter uma instalação do OJS de sucesso: efetuar o download e extrair os ficheiros de aplicação do OJS para um diretório do seu servidor que seja acessível na Web; criar um ficheiro /diretório separado que não seja acessível na Web; e muito provavelmente, criar manualmente uma base de dados de utilizadores e base de dados.

### Nota
> Todos os servidores são diferentes, e o seu processo de instalação pode ser diferente de outro servidor. Se algo não funcionar corretamente, verifique a documentação que acompanha o OJS no docs/ folder, bem como o fórum de suporte e as FAQ. Mas também não se esqueça de ler também a documentação do seu servidor e fornecedor de servidor.


## Download e extração do Ficheiro de Instalação OJS

Todos os downloads do OJS podem ser encontrados em http://pkp.sfu.ca/ojs_download. Dependendo das suas circunstâncias poderá preferir efetuar o download ou da versão mais recente estável (melhor para sistemas em produção) ou a versão mais recente de desenvolvimento (menos estável mas com mais recursos). O processo de instalação é igual para ambas as versões.

Extraia o ficheiro tar, e coloque os conteúdos extraídos para um diretório acessível na web no seu servidor web onde pretende correr o OJS. Um diretório comum acessível na web é /var/www/html, o qual será utilizado como exemplo.

### Nota

> Relativamente a diretórios acessíveis na web: cada servidor é diferente. Se não sabe onde se encontra o seu diretório acessível na web (isto é, o diretório onde colocar tudo que pretende que fique visível ao público no seu site; por vezes chamado de diretório web root), deverá contactar o seu fornecedor do serviço.

Se não descarregar o ficheiro tar diretamente para o ser servidor web, pode extrair o ficheiro tar para o seu computador e transferir os seus conteúdos por FTP, ou pode transferir o ficheiro tar por FTP para o seu servidor web e correr o seguinte comando:

```
tar xzf ./ojs-3.00.tar.gz
```

Isto irá extrair os ficheiros do OJS para o diretório /var/www/html/ojs-3.00. Pode alterar o nome do diretório para outro mais amigável, tal como "ojs". Neste ponto, estará pronto a entrar nesse diretório no seu servidor, (ie. entrar no seu browser em http://example.com/ojs/) e ver o écrã de instalação.


## Preparar o seu Ambiente para Instalação

Vai necessitar de criar um diretório para o OJS armazenar os ficheiros das submissões. Este diretório não deve acessível via web, senão ficheiros privados poderiam ficar acessíveis online (ex. por utilizadores experientes tentando aceder diretamente ao documento inserindo no browser http://www.example.com/files/journals/1/articles/1/submission/review/1-3-1-RV.doc). Se, por exemplo, tiver colocado os ficheiros da aplicação do OJS em /var/www/html/ojs/, terá de criar fora um diretório /var/www/.

Depois terá de atribuir permissões para que o servidor web possa administrar e editar os subdiretórios public/ e cache/ do caminho da instalação do OJS,  o diretório files/ que acabou de criar, e o ficheiro de configuração config.inc.php. As especificações da configuração de permissões irá depender da configuração do seu servidor web, i.e. se os scripts PHP correm SetUID. A página de instalação irá avisá-lo se não tiver as permissões adequadas.

No exemplo acima, config.inc.php não era editável pelo servidor (o que não é estritamente necessário para o funcionamento normal, apesar de ser para a instalação automática), e nem o diretório cache/t_cache/. Lembre-se que todos os diretórios dentro do cache/ devem ser editáveis pelo servidor.

##Configure a Informação da sua Base de Dados

Será necessário criar uma base de dados para o sistema usar, e assegurar que tem um utilizador de base de dados com permissões suficientes para gerir a base de dados. O OJS consegue correr diferentes tipos de RDBMS, apesar de apenas PostgreSQL e MySQL terem sido ativamente testados.

Para o MySQL, pode criar a base de dados e o utilizador através do phpMyAdmin ou da interface da linha de comandos do MySQL. Segue-se um exemplo CLI:
```
$ mysql -u root -p
Enter password: 

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 95
Server version: 5.1.38 MySQL Community Server (GPL)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CREATE DATABASE ojs DEFAULT CHARACTER SET utf8;
Query OK, 1 row affected (0.13 sec)

mysql> GRANT ALL ON ojs.* TO pkpuser@localhost IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.15 sec)

mysql> exit;
Bye
```
Neste exemplo, a base de dados tem o nome de ojs; o utilizador da base de dados tem o nome de pkpuser; e a password é password (certamente nada segura!). Irá necessitar destas três informações mais tarde.

## Complete a Instalação através da Web

Através do seu browser aceda ao diretório de instalação do OJS. Aparecer-lhe-á uma página de instalação para a instalação do OJS: preencha todos os campos do formulário (incluindo a informação de conexão à base de dados que estabeleceu anteriormente; e em Configurações de Ficheiros, a localização do caminho dos ficheiro que criou anteriomente) e clique em Instalar no final da página.

Deverá configurar as configurações de idioma do seu site: não apenas os idiomas disponíveis aos utilizadores, mas também as opções de conjuntos de caracteres. Se possível, altere do padrão para "Unicode (UTF-8)". A menos que o servidor da base de dados seja particularmente antigo, não deve ter problemas ao configurar estas opções para Unicode. Esta alteração irá assegurar melhor suporte para vários idiomas.

Depois deverá especificar a localização do diretório files/ que criou anteriormente.

Em seguida, escolha as suas configurações de segurança. Esta opção de configuração especifica como é que o sistema armazena as passwords.SHA1 é mais seguro que MD5, por isso se a sua versão PHP é 4.3.0 ou superior, escolha a opção SHA1.

Depois terá de especificar um nome de utilizador, password e e-mail para a Conta de Administrador. No final da instalação com sucesso, use esta conta para se autenticar e configurar novas revistas; mas geralmente esta conta não é utilizada para a gestão diária de uma revista.

A seguir é a secção de Configurações da Base de Dados. Deve preencher corretamente as configurações de conexão à base de dados: escolha a driver da base de dados correta para o seu sistema; especifique a host correta (normalmente localhost, mas pode ser diferente dependendo da sua configuração); o username e password para o utilizador da base de dados; e o nome da base de dados a que este se irá conectar. Se ainda não criou a base de dados, assegure-se que a opção "Criar nova base de dados" continua ativa; no entanto, esta opção não irá funcionar se o utilizador da base de dados não tiver permissões suficientes para criar bases de dados, e neste caso deverá criar a base de dados antecipadamente.

##Instalação do OJS: Configurações da Base de dados

Em seguida, escolha o identificador de repositório OAI apropriado (o padrão é suficiente), e escolha a opção Instalar Open Journal Systems se o seu utilizador puder editar diretamente a base de dados; ou Instalação Manual se for necessário editar a base de dados manualmente.

Se tudo correr bem, irá aparecer um ecrã de sucesso.

Se o seu ficheiro config.inc.php file não for editável pelo servidor, ser-lhe-á solicitado que copie os conteúdos para um campo de texto e cole no ficheiro config.inc.php no servidor.

Se escolher a Instalação Manual, ser-lhe-á solicitado a cópia de vários SQL statements, que devem ser executados a partir do seu servidor SQL.