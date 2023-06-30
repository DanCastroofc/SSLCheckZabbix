# Documentação do Script de Monitoramento de Certificados SSL para Zabbix

Este documento descreve como utilizar o script de monitoramento de certificados SSL para o Zabbix. O script permite monitorar a validade de certificados SSL em servidores remotos e obter alertas quando os certificados estão próximos da expiração.

## Requisitos

- Servidor Zabbix instalado e em funcionamento.
- Acesso aos servidores remotos que serão monitorados.
- Permissões adequadas para executar scripts no servidor Zabbix.

## Passo 1: Preparação

1. Faça o download do script de monitoramento de certificados SSL. Você pode salvá-lo em qualquer diretório em seu servidor Zabbix.

2. Torne o script executável com o seguinte comando:
   ```
   chmod +x nome_do_script.sh
   ```

## Passo 2: Configuração no Zabbix

1. Faça login na interface web do Zabbix.

2. Acesse a seção "Configuration" e clique em "Templates".

3. Clique em "Create template" para criar uma nova template.

4. Defina um nome para a template, por exemplo, "Monitoramento SSL".

5. Na guia "Items", clique em "Create item" para adicionar um novo item à template.

6. Preencha os seguintes campos:
   - Name: Nome do item (por exemplo, "Validade do Certificado SSL").
   - Type: Selecione "External check".
   - Key: Caminho completo para o script de monitoramento (por exemplo, "/caminho/para/o/script.sh {HOST.DNS}").
   - Type of information: Selecione "Numeric (unsigned)".
   - Update interval: Defina o intervalo de atualização desejado para o monitoramento.
   - Applications: Selecione ou crie uma aplicação relevante para o monitoramento.

7. Na guia "Triggers", você pode adicionar gatilhos para alertas com base nos valores obtidos pelo script. Por exemplo, você pode configurar um gatilho para disparar um alerta quando a validade do certificado for menor que 30 dias.

8. Clique em "Add" para adicionar a template.

## Passo 3: Associação ao Host

1. Acesse a seção "Configuration" e clique em "Hosts".

2. Selecione o host ao qual deseja associar a template.

3. Na guia "Templates", clique em "Link new templates".

4. Selecione a template "Monitoramento SSL" (ou o nome que você atribuiu) e clique em "Select".

5. Clique em "Add" para associar a template ao host.

## Testando o Monitoramento

Após a configuração, o Zabbix começará a executar o script de monitoramento nos servidores remotos de acordo com o intervalo definido. Os valores obtidos pelo script serão registrados e poderão ser visualizados nos gráficos e gatilhos configurados.

Para testar manualmente o script de monitoramento, você pode executá-lo no servidor Zabbix com o seguinte comando:
```
./nome_do_script.sh nome_do_servidor
```
Substitua "nome_do_script.sh" pelo nome do seu script e "nome_do_servidor" pelo endereço do servidor que deseja verificar.

## Conclusão

Com a template de monitoramento de certificados SSL configurada no Zabbix e o script de monitoramento em funcionamento, você poderá acompanhar a valid
