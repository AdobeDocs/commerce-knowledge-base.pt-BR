---
title: Não é possível alterar o mecanismo de pesquisa em "app/etc/env.php"
description: Este artigo fornece uma solução para o problema em que você tenta alterar o mecanismo de pesquisa no Administrador do Commerce, mas os campos estão bloqueados.
exl-id: 61006ce7-34f9-4e4d-a197-f3d627dd277f
source-git-commit: c903360ffb22f9cd4648f6fdb4a812cb61cd90c5
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Não é possível alterar o mecanismo de pesquisa no `app/etc/env.php`

Este artigo fornece uma solução para o problema em que você tenta remover a configuração do mecanismo de pesquisa do `app/etc/env.php` arquivo, mas após a reimplantação, a configuração é revertida para a configuração anterior ou é alterada para [!DNL OpenSearch] por padrão.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, [todas as versões compatíveis](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Você tenta alterar o mecanismo de pesquisa no Commerce Admin, mas os campos estão bloqueados.

## Causa

A configuração do mecanismo de pesquisa está bloqueada na variável `app/etc/env.php` ou o mecanismo de pesquisa é explicitamente definido na variável `.magento.env.yaml` arquivo.

## Solução

1. Verifique a `.magento.env.yaml` arquivo no estágio de implantação e veja se a variável `SEARCH_CONFIGURATION` foi configurada. Exemplo:

   ```yaml
   SEARCH_CONFIGURATION:
     engine: elasticsearch7
     ...
   <VARIABLE X>
   ```

1. É o  `SEARCH_CONFIGURATION` variável presente? Se não estiver presente, a configuração do mecanismo de pesquisa será bloqueada para [!DNL OpenSearch] por padrão. Para alterar a configuração, você deve adicionar a variável ao `.magento.env.yaml` arquivo com o valor apropriado para o mecanismo de pesquisa. Se a variável `SEARCH_CONFIGURATION` estiver presente e você quiser modificar o mecanismo, substitua o valor existente do mecanismo em `.magento.env.yaml`. Valores possíveis/conhecidos: [!DNL opensearch], [!DNL livesearch], [!DNL elasticsuite], [!DNL amasty_elastic], e [!DNL amasty_elastic_opensearch].
1. Reimplante a instância.
1. O campo do mecanismo de pesquisa no Admin permanecerá bloqueado, mas deve ser atualizado com o valor especificado.

## Leitura relacionada

* [Campos bloqueados no administrador do Commerce](/help/troubleshooting/miscellaneous/locked-fields-in-magento-admin.md) no Guia de infraestrutura do Commerce na nuvem.
