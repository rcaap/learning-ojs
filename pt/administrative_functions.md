# Funções Administrativas

Esta secção fornece informação detalhada sobre o servidor onde o OJS se encontra a correr.
![](/assets/learning-ojs3.1-sa-admin-functions.PNG)

## Informações sobre o Sistema

Useesta secção para encontrar detalhes sobre o servidor onde corre a sua instalação.

![](/assets/learning-ojs3.1-sa-sysinfo.PNG)

Informação sobre a Versão do OJS mostra-lhe que versão se encontra atualmente instalada, e o seu histórico de versões incluindo todas as atualizações. Ao clicar em Pesquisar Atualizações pode ver se está a utilizar a versão mais recente do OJS.


As Informações do Servidor fornecem detalhes sobre o servidor que hospeda a sua instalação do OJS.

A secção da Configuração do OJS disponibiliza todas as opções de configuração e os seus valores como estão em _config.inc.php_.

Pode encontrar mais informações sobre os parâmetros de configuração do _config.inc.php_ no próprio ficheiro.

A secção final nesta página exibe informação adicional sobre o sevidor: o sistema operacional, versão do PHP, informação do serviço e da base de dados. Também pode ver informação adicional sobre o PHP ao clicar no link Extended PHP Information \(exibe o output do phpinfo\(\)\).

Todas estas informações podem ser úteis ao tentar resolver algum problema. 

## Expirar Sessões de Utilizadores

Ao clicar em _Expirar Sessões de Utilizadores_ imediatamente fecha todas as sessões de utilizadores no sistema, fazendo com que qualquer utilizador com conta iniciada terá que se autenticar de novo. Esta funcionalidade pode ser útil antes de uma atualização, para assegurar que não há utilizadores autenticados.

## Limpar Cache de Dados

Ao clicar em _Limpar Cache de Dados_ limpa todos os dados na cache, incluindo informação de idioma, cache de ajuda, e cache de pesquisa. Esta função pode ser útil para forçar os dados a recarregarem depois de terem sido feitas configurações.

## Limpar Cache de Template 

Ao clicar em _Limpar Cache de Template_ limpar a cache de todas as versões de templates de HTML. Esta função pode ser útil para forçar os templates a recarregarem depois de terem sido feitas configurações.

## Limpar logs de execução da tarefa

Se tiver ativas tarefas agendadas, ao clicar em _Limpar logs de execução de tarefa_ irá eliminar os ficheiros de logs do seu servidor. Os ficheiros log de execução incluem datas que correspondem a tarefas anteriormente concluídas \(ex. enviar lembretes automáticos aos revisores\).