# DTD_ARQINV_ReporterUniversal

Processo responsável por fazer um relatório por meio das informações contidas nos itens de fila de todos os demais processos Vibra executados.

## Automação: Informações de configuração.
### 1. PRODUÇÃO
#### 1.1. Assets
Nome|Tipo
-|-
UiPathOrchestrator_URL|String
SMTP_URL|String
OFFICE365_APPID|String
OFFICE365_TENANT|String

#### 1.2. Queues
Nome|Unique Ref.|Auto Retry
:-|:-:|:-:
DTD_ARQINV_ReporterUniversal|Não há|Não há

#### 1.3. Parâmetros
Nome|Tipo|Valor|Descrição
:-|:-:|-:|-|
in_orchestratorQueueNameReporter|String|DTD_ARQINV_ReporterUniversal|Nome da fila do Reporter Universal na qual os itens serão buscados para serem reportados
in_credentialOrcOnPrem|String|braxOrcOnPrem|Nome do asset que armazena as credenciais do Brax para as requisições de api no Orquestrador
in_tenantName|String|Default|Nome da tenant dentro do orquestrador na qual o processo irá executar e buscar as informações necessárias
in_credentialBraxMail|String|braxMailSender|Nome do asset que armazena as credenciais para envio de email Microsoft Office 365 do Brax
in_sendMailToBusinessArea|Boolean|True ou False a ser escolhida na execução|Variável booleana responsável pelo envio do report para as áreas de negócios
in_emailReceiverCc|String|brdistribuidora-rpa-logs@smarthis.com.br|Possíveis e-mails fixos que deverão receber em cópia os relatórios enviados. Exemplo: brdistribuidora-rpa-logs@smarthis.com.br
in_orchestratorQueueShouldProcessReport|String|Pode ou não ser preenchido a depender da execução|Se for necessário que o Reporter Universal gere um novo queueItem específico para processamento, este campo deverá ser preenchido. Caso contrário, deve ser vazio.
in_emailReceiverBusinessArea|String|Pode ou não ser preenchido a depender da execução|Lista de e-mails da área de negócios que deverão receber o relatório após a execução da automação **caso o argumento in_orchestratorQueueShouldProcessReport esteja preenchido**. A lista deve ser string com os e-mails separados por ;

### 2. HOMOLOGAÇÃO
#### 2.1. Assets
Nome|Tipo
-|-
UiPathOrchestrator_URL|String
SMTP_URL|String
OFFICE365_APPID|String
OFFICE365_TENANT|String

#### 2.2. Queues
Nome|Unique Ref.|Auto Retry
:-|:-:|:-:
DTD_ARQINV_ReporterUniversal|Não há|Não há

#### 2.3. Parâmetros
Nome|Tipo|Valor|Descrição
:-|:-:|-:|-|
in_orchestratorQueueNameReporter|String|DTD_ARQINV_ReporterUniversal|Nome da fila do Reporter Universal na qual os itens serão buscados para serem reportados
in_credentialOrcOnPrem|String|braxOrcOnPrem|Nome do asset que armazena as credenciais do Brax para as requisições de api no Orquestrador
in_tenantName|String|Default|Nome da tenant dentro do orquestrador na qual o processo irá executar e buscar as informações necessárias
in_credentialBraxMail|String|braxMailSender|Nome do asset que armazena as credenciais para envio de email Microsoft Office 365 do Brax
in_sendMailToBusinessArea|Boolean|True ou False a ser escolhida na execução|Variável booleana responsável pelo envio do report para as áreas de negócios
in_emailReceiverCc|String|brdistribuidora-rpa-logs@smarthis.com.br|Possíveis e-mails fixos que deverão receber em cópia os relatórios enviados. Exemplo: brdistribuidora-rpa-logs@smarthis.com.br
in_orchestratorQueueShouldProcessReport|String|Pode ou não ser preenchido a depender da execução|Se for necessário que o Reporter Universal gere um novo queueItem específico para processamento, este campo deverá ser preenchido. Caso contrário, deve ser vazio.
in_emailReceiverBusinessArea|String|Pode ou não ser preenchido a depender da execução|Lista de e-mails da área de negócios que deverão receber o relatório após a execução da automação **caso o argumento in_orchestratorQueueShouldProcessReport esteja preenchido**. A lista deve ser string com os e-mails separados por ;

### 2. Especificações do projeto

## Tipo de execução

O processo acontece inteiramente em background, tendo uma boa assertividade e uma boa agilidade.

## Geração de um item de fila especificado para report

Caso haja necessidade de reportar um processo específico em algum horário definido deve-se preencher os seguintes argumentos in_orchestratorQueueShouldProcessReport, in_emailReceiverBusinessArea. O argumento in_orchestratorQueueShouldProcessReport é responsável por ditar se o item será ou não adicionado na fila do reporter universal para processamento, se o argumento for vazio ou nulo, nem um item é adicionado, se o argumento for preenchido um novo item será adicionado para processamento. As pessoas que receberão o e-mail referente ao item específico gerado serão as que estão especificadas no argumento in_emailReceiverBusinessArea.

## Argumento in_emailReceiverCc

Argumento utilizado unicamente para e-mails fixos que deverão receber o acompanhamento dos relatórios de todos os projetos Vibra. Hoje em dia temos o de logs para acompanhamento de sucesso dos projetos.