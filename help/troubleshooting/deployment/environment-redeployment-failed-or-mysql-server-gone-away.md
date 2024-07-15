---
title: Falha na reimplantação do ambiente ou o servidor MySQL desapareceu
description: Este artigo fornece uma solução para problemas do Adobe Commerce (todos os métodos de implantação), em que a interrupção do espaço alocado para o MySQL causa erros de implantação travada ou de conexão de banco de dados.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Falha na reimplantação do ambiente ou o servidor MySQL desapareceu

Este artigo fornece uma solução para problemas do Adobe Commerce (todos os métodos de implantação), em que a interrupção do espaço alocado para o MySQL causa erros de implantação travada ou de conexão de banco de dados.

## Produtos e versões afetados

* Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem (todas as versões)

## Problema

* O processo de implantação falha com o seguinte erro no log de implantação (linha de comando e log de interface do usuário): ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* O Adobe Commerce responde com o erro 503, e a seguinte mensagem de erro é exibida nos logs de aplicativos:    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    e o seguinte erro é exibido quando você se conecta a um servidor MySQL:    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Causa

A causa mais provável dos problemas é o espaço alocado no banco de dados MySQL estar muito baixo. Para garantir que esse seja o caso, verifique o espaço disponível para o MySQL conforme descrito mais detalhadamente.

### Verificar se há espaço suficiente para o MySQL

Para todos os ambientes de arquitetura de plano inicial do Adobe Commerce na infraestrutura em nuvem e [Ambiente de integração](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) da arquitetura de plano Pro do Adobe Commerce na infraestrutura em nuvem, [SSH para o ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) e execute o comando:

```bash
magento-cloud db:size
```

Para o ambiente de preparo ou produção da arquitetura Pro, [SSH para o ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html), e execute o `df -h`   Comando `| grep mysql`. O resultado será semelhante ao seguinte:

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Solução

### Para resolver o problema, você precisa alocar mais espaço para o MySQL.

Para todos os ambientes de Integração de arquitetura Starter e Pro, isso é feito no arquivo `.magento/services.yaml`, aumentando o parâmetro `mysql: disk:`. Por exemplo:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Consulte o artigo [Configurar serviço MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html) para referência.

Para fazer essas alterações para o ambiente de preparo ou produção da arquitetura Pro, você deve criar um [Tíquete de suporte](https://support.magento.com). Mas normalmente, você não precisará lidar com isso no armazenamento temporário/produção da arquitetura Pro, pois o Adobe Commerce monitora esses parâmetros para você e o alerta e/ou executa ações de acordo com o contrato.

### Aplicar as alterações

Depois de alterar o arquivo `.magento/services.yaml`, você precisa confirmar e enviar suas alterações para que elas sejam aplicadas. O push acionará o processo de implantação.
