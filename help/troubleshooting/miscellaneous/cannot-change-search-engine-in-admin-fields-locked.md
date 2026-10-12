---
title: Não é possível alterar o mecanismo de pesquisa em "app/etc/env.php"
description: Este artigo fornece uma solução para o problema em que você tenta alterar o mecanismo de pesquisa no Administrador do Commerce, mas os campos estão bloqueados.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%
---
# Não é possível alterar o mecanismo de pesquisa em `app/etc/env.php`

Este artigo fornece uma solução para o problema em que você tenta remover a configuração do mecanismo de pesquisa do arquivo `app/etc/env.php`, mas após a reimplantação, a configuração é revertida para a configuração anterior ou alterada para [!DNL OpenSearch] por padrão.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões com suporte](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Você tenta alterar o mecanismo de pesquisa no Commerce Admin, mas os campos estão bloqueados.

## Causa

A configuração do mecanismo de pesquisa está bloqueada no arquivo `app/etc/env.php` ou o mecanismo de pesquisa está explicitamente definido no arquivo `.magento.env.yaml`.

## Solução

1. Verifique o arquivo `.magento.env.yaml` no estágio de implantação e veja se a variável `SEARCH_CONFIGURATION` foi configurada. Exemplo:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. A variável `SEARCH_CONFIGURATION` está presente? Se não estiver presente, a configuração do mecanismo de pesquisa será bloqueada para [!DNL OpenSearch] por padrão. Para alterar a configuração, você deve adicionar a variável ao arquivo `.magento.env.yaml` com o valor apropriado para o mecanismo de pesquisa. Se a variável `SEARCH_CONFIGURATION` estiver presente e você quiser modificar o mecanismo, substitua o valor existente do mecanismo em `.magento.env.yaml`. Valores possíveis/conhecidos: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic] e [!DNL amasty_elastic_opensearch].
1. Reimplante a instância.
1. O campo do mecanismo de pesquisa no Admin permanecerá bloqueado, mas deve ser atualizado com o valor especificado.

## Leitura relacionada

* [Campos bloqueados (esmaecidos) no Commerce Admin](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-26879) no Guia de Infraestrutura do Commerce na Nuvem.
