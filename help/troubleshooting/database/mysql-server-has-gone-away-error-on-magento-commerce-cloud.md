---
title: O servidor MySQL desapareceu​ erro no Adobe Commerce na nuvem
description: Este artigo fala sobre a solução do problema em que você recebe uma mensagem de erro "O servidor SQL desapareceu*" no arquivo "cron.log". Pode haver vários sintomas, incluindo problemas de importação de arquivos de imagem ou falha de implantação.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# O servidor MySQL desapareceu&#x200B; erro no Adobe Commerce na nuvem

Este artigo fala sobre a solução do problema em que você recebe a mensagem de erro &quot; *O SQL Server desapareceu* &quot; no arquivo `cron.log`. Pode haver vários sintomas, incluindo problemas de importação de arquivos de imagem ou falha de implantação.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as [versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf).

## Problema

Você recebe uma mensagem de erro &quot; *O SQL Server desapareceu* &quot; no arquivo `cron.log`.

<u>Etapas a serem reproduzidas</u>

Importe arquivos e acione uma implantação.

<u>Resultado esperado</u>

Implantação bem-sucedida.

<u>Resultado real</u>

Mensagem de erro em `cron.log` :&quot; *SQLSTATE\[HY000\] \[2006\] O servidor MySQL foi desativado at/app/AAAAAAAAA/vendor/magento/zendframework1/library/Zend/Db/Adapter/Pdo/Abstract.php:144&quot;*

## Causa

O valor `default_socket_timeout` está definido como muito baixo. Isso é causado pela configuração `default_socket_timeout`. Se o php não receber nada do banco de dados MySQL dentro deste período, ele assume que está desconectado e emite o erro.

## Solução

1. Verifique o período de tempo limite atual para `default_socket_timeout` executando na CLI:    ```    php -i |grep default_socket_timeout    ```
1. Dependendo do aumento da configuração de tempo limite, a variável `default_socket_timeout` ultrapassará o tempo de execução mais longo possível esperado no arquivo `/etc/platform/<project_name>/php.ini`. Sugere-se que você defina entre 10 e 15 minutos.
1. Confirme-o no GIT e reimplante.

## Leitura relacionada

* [O upload do banco de dados perde a conexão com o MySQL](/help/troubleshooting/database/database-upload-loses-connection-to-mysql.md)
* [Práticas recomendadas do banco de dados para o Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html?lang=pt-BR)
* [Problemas mais comuns de banco de dados no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=pt-BR)
