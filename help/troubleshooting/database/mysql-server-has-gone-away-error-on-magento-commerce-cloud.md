---
title: O servidor MySQL desapareceu​ erro no Adobe Commerce na nuvem
description: Este artigo fala sobre a solução do problema em que você recebe uma mensagem de erro "O servidor SQL desapareceu*" no arquivo "cron.log". Pode haver vários sintomas, incluindo problemas de importação de arquivos de imagem ou falha de implantação.
exl-id: 14cb9a6d-6d25-4044-8f52-d65648c03431
feature: Cloud, Paas, Services, Variables
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '312'
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

1. Verifique o tempo limite atual para `default_socket_timeout` executando na CLI: `php -i |grep default_socket_timeout`.
1. Verifique o tempo limite atual para `default_socket_timeout` executando na CLI: `php -i |grep default_socket_timeout`
1. Dependendo do aumento da configuração de tempo limite, a variável `default_socket_timeout` ultrapassará o tempo de execução mais longo possível esperado no arquivo `/etc/platform/<project_name>/php.ini`. Sugere-se que você defina entre 10 e 15 minutos.
1. Confirme-o no GIT e reimplante.

## Leitura relacionada

* [Práticas recomendadas de banco de dados para o Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/database-on-cloud.html)
* [Problemas mais comuns de banco de dados no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html)
