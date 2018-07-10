# Atualização

Nota: Antes de atualizar o seu sistema, efetue um backup completo dos seus ficheiros de dados e da base de dados. Se o processo de atualização falhar, será necessário recuperar o backcup antes de continuar.

Se estiver a usar o Modo Seguro do PHP, assegure-se que a diretiva max_execution_time no seu ficheiro de configuração php.ini está configurado para o limite máximo. Se este ou outro limite de tempo (ex. diretiva Apache's "Timeout") for atingido e o processo interrompido, será necessária intervenção manual.


##Atualizar do OJS 2.0.x, 2.1.x, 2.2.x, or 2.3.x

De forma a atualizar a partir destas versões mais antigas do OJS, é obrigatório atualizar primeiro para uma versão intermédia do OJS 2.4.x. Faça o download da cópia mais recente do OJS 2.4.x e siga as instruções de atualização incluídas, depois leia o documento docs/UPGRADE incluído no pacote para continuar a atualizar a partir daqui.


##Atualizar do OJS 2.4.x

O OJS 3.x é uma grande mudança no Open Journal Systems, introduzindo vários novos conceitos e diferentes abordagens. O processo de atualização do 2.x para o 3.x tenta adaptar o conteúdo antigo às novas estruturas da melhor forma possível, mas recomendamos fortemente efetuar um teste de atualização e explorar o novo sistema antes de comprometer o seu conteúdo na atualização. Downgrades de da versão 3.x para a 2.x não são suportados.

Atualizar para a versão mais recente do OJS envolve dois passos:

    - Obter o código mais recente do OJS
    - Atualizar a base de dados do OJS

É altamente recomendado que também reveja as notas de lançamento (docs/RELEASE) e outra documentação no diretório de documentos antes de efetuar atualização.


## Obter o código mais recente do OJS

O código-fonte do OJS encontra-se disponível de duas formas: um pacote completo autónomo, e  através da área do github somente para leitura.

1) Pacote Completo

Também é possível atualizar efetuando o download do pacote completo para a última versão do OJS:

    - Efetuar download e extrair o pacote a partir do website do OJS
    - Efetuar uma cópia do config.inc.php fornecido no novo pacote
    - Movee ou copiar os seguintes ficheiros e diretórios da sua instalação atual do OJS :
        - config.inc.php
        - public/
        - O seu diretório de ficheiros de upload ("files_dir" em config.inc.php), se estiver dentro do seu diretório do OJS
    - Substitua o diretório atual do OJS pelo novo diretório do OJS, movendo o antigo para um local seguro como backup
    - Assegure-se que revê a secção Alterações de Configuração nas notas de lançamento em docs/release-notes/README-(version) para todas as versões entre a sua de origem e a nova versão. Pode necessitar de adicionar manualmente novos ítens ao seu ficheiro config.inc.php file.

Atualizar a partir do github é a abordagem recomendada se efetuou alterações locais ao sistema.

2) git


Se a sua instância foi retirada do github (ver docs/README-GIT), pode atualizar o código do OJS utilizando um cliente git.

Para atualizar o código do OJS a partir de um git, corra o seguinte comando a partir do seu diretório OJS:

    $ git rebase --onto <new-release-tag> <previous-release-tag>

Este comando assume que fez alterações locais e inseriu-as por cima da versão anterior. O comando irá pegar nas suas alterações personalizadas e aplicá-las na nova versão. Isto pode causar conflitos que terão de ser resolvidos da forma habitual, ex. utilizando uma ferramenta de merge como kdiff3.

"TAG" deve ser substituído com a tag do git correspondente à nova versão. As tags das versões do OJS têm o formato "ojs-MAJOR_MINOR_REVSION-BUILD". Por exemplo, a tag para a versão inicial do OJS 3.0.0 é "ojs-3_0_0-0".

Consulte o ficheiro README do pacote do OJS mais recente ou o website do OJS para saber a tag correspondente à última versão disponível do OJS.

Note que tentar atualizar para uma versão ainda não disponível (ex., usando a tag HEAD para obter o código do OJS de ponta) não é recomendável para ninguém além de programadores do OJS ou externos; usar código experimental num desenvolvimento em produção é altamente desencorajado e não será apoiado de qualquer maneira pela equipa do OJS.


## Atualizar a base de dados do OJS

Depois de obter o código mais recente do OJS, um script adicional deve ser corrido para completar o processo de atualização através da atualização da base de dados e potencialmente executando código de atualização adicional.

Este script pode ser executado através da linha de comandos ou através da interface web do OJS.

1) Linha de comandos

Se tiver a versão CLI do PHP instalada (ex., /usr/bin/php), pode atualizar a sua base de dados através dos seguintes passos:

    - Editar config.inc.php e alterar "installed = On" para "installed = Off"
    - Correr o seguinte comando a partir do diretório do OJS (não incluir o $):
      $ php tools/upgrade.php upgrade
    - Reeditar config.inc.php e alterar "installed = Off" de volta para 
       "installed = On"

2) Web

Se não tem o PHP CLI instalado, pode atualizar correndo um script através da web. Para isso:

    - Editar config.inc.php e alterar "installed = On" para "installed = Off"
    - Abrir um browser e seguir para o seu site OJS; deverá ser direcionado para a página de instalação e atualização
    - Selecionar o link "Upgrade" e seguir as instruções presentes no ecrã
    - Reeditar o config.inc.php e alterar "installed = Off" de volta para
       "installed = On"