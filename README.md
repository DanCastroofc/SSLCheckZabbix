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
  

##Passo 2: Configuração no Zabbix

1. Faça o download da template `SSL_Check_Template.yaml`.
2. Faça login na interface web do Zabbix.
3. Acesse a seção "Configuration" e clique em "Templates".
4. Clique em "Importar" e selecione a template baixada.
  

## Passo 3: Associação ao Host

1. Acesse a seção "Configuration" e clique em "Hosts".
2. Selecione o host ao qual deseja associar a template.
3. Na guia "Templates", clique em "Link new templates".
4. Selecione a template "SSL Check" e clique em "Select".
5. Clique em "Add" para associar a template ao host.
6. Clique na aba "Macros".
7. Clique em "Macros herdados e do Host".
8. Procure pela macro `{$SSL_HOST}` e clique em "Modificar".
9. Agora volte para a aba "Macros de Host".
10. No campo "Valor" da macro `{$SSL_HOST}`, digite o DNS do site que deseja monitorar.
  
  - Exemplo: www.meu-site.com.br
11. Clique em "Atualizar".
  

## Testando o Monitoramento

Após a configuração, o Zabbix começará a executar o script de monitoramento nos servidores remotos de acordo com o intervalo definido. Os valores obtidos pelo script serão registrados e poderão ser visualizados nos gráficos e gatilhos configurados.

Para testar manualmente o script de monitoramento, você pode executá-lo no servidor Zabbix com o seguinte comando:

```
./checkssl.sh nome_do_servidor
```

Substitua "nome_do_script.sh" pelo nome do seu script e "nome_do_servidor" pelo endereço do servidor que deseja verificar.

## Conclusão

Com a template de monitoramento de certificados SSL configurada no Zabbix e o script de monitoramento em funcionamento, você poderá acompanhar a valid
