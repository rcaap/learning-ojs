# Instalação

O Open Journal Systems \(OJS\) é um software desenvolvido pelo Public Knowledge Project.  
Para informações gerais sobre o OJS e outros sistemas de invesstigação visite o  
o site do PKP em [http://pkp.sfu.ca/](http://pkp.sfu.ca/).

## Licença

OJS encontra-se licenciado sob GNU General Public License v2. Veja o ficheiro  
docs/COPYING para os termos completos desta licença.

Todas as contribuições para modificações e redistribuição do OJS por inteiro ou faseado são bem-vindas  
de acordo com os termos desta licença. according to the terms of this license. PKP também agradece o envio de  
melhorias ou correções de erros do software.

## Requisitos do Sistema

Requisitos do servidor recomendados:

* PHP &gt;= 5.5 com suporte de MySQL ou PostgreSQL
* MySQL &gt;= 4.1 ou PostgreSQL &gt;= 9.1.5
* Apache &gt;= 1.3.2x or &gt;= 2.0.4x ou Microsoft IIS 6
* Sistema operativo: Qualquer OS que suporte o software referido acima, incluindo 
  Linux, BSD, Solaris, Mac OS X, Windows

Como o PKP não possui recursos para testar todas as combinações possíveis de  
versões de software e plataformas, não há garantia da operação certa ou suporte   
Agradecemos os comentários dos utilizadores que implantaram o OJS  
noutros sistemas que não os apresentados acima.

## Configuração Recomendada

Para obter uma implementação segura deverá seguir as seguintes políticas:

* Dedicar uma base de dados ao OJS; use credenciais únicas para o acesso.  
  Configure esta base de dados para executar backups automáticos com regularidade  
  Efetue um backup manual quando atualizar o sistema ou realizar manutenção.  
  
* Configure o OJS \(config.inc.php\) para usar SHA1 hashing em vez de MD5.

* Configure o OJS \(config.inc.php\) para usar force\_ssl\_login para que os  
  utilizadores autenticados comuniquem com o servidor via HTTPS.

* Instale o OJS para que os ficheiros do diretório NÃO sejam um subdiretório da  
  instalação do OJS e não possa ser acedida diretamente através do servidor web  
  Retrinja as permissões aos ficheiros o máximo possível. Backups automáticos  
  deste diretório devem estar sincronizados com os backups da base de dados.  
  Estes passos são **fundamentais para manter um ambiente seguro**   
  e evitar o uso indevido ou o hacking da revista.

## Download

O OJS está disponível para download no [site do Public Knowledge Project.](http://pkp.sfu.ca)

## Instalação

Reveja este documento e o documento da VERSÃO LANÇADA anterior para instalar o OJS.  Se tiver dificuldades, veja também o documento FAQ neste diretório.

Para instalar o OJS:

1. Extraia o arquivo do OJS para a localização pretendida no seu diretório de   
  documentos na web.

2. Torne os seguintes ficheiros e diretórios \(e os seus conteúdos\)  
   editável\(i.e., mudando o proprietário ou as permissões com chown ou  
   chmod\):

   * config.inc.php \(opcional -- se não estiver editável ser-lhe-á solicitado 
     para substituir este ficheiro manualmente durante a instalação\)
   * public
   * cache
   * cache/t\_cache
   * cache/t\_config
   * cache/t\_compile
   * cache/\_db

3. Crie um diretório para armazenar os ficheiros enviados para o sistema \(ficheiros de submissão, etc.\)  
   e torne este diretório editável. É **altamente** recomendado que este diretório  
   se encontre numa localização não acessível pela web para assegurar um ambiente  
   seguro  \(ou protegido do acesso direto, tal como via .htaccess rules\).

4. Abra num browser o link [http://yourdomain.com/path/to/ojs/](http://yourdomain.com/path/to/ojs/) e  
   siga as instruções de instalação que aparecem no écrã.

   Em alternativa, o command-line installer pode ser usado em vez de
   correr o comando "php tools/install.php" no seu diretório OJS.  
   \(Nota: com o CLI installer pode necessitar chown/chmod ao diretório de   
   ficheiros públicos e enviados para o sistema após a instalação, se o utilizador de  
   Apache for diferente do utilizador a correr a ferramenta.\)

5. Passos adicionais recomendados pós-instalação:

   * Rever config.inc.php para configurações adicionais
   * Rever o documento FAQ para questões técnicas e de configuração de servidor mais frequentes.



