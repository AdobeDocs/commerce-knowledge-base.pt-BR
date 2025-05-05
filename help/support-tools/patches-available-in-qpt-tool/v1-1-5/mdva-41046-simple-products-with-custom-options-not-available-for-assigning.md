---
title: 'MDVA-41046: produtos simples com opções personalizadas não disponíveis para atribuição'
description: O patch MDVA-41046 resolve o problema em que produtos simples com opções personalizadas não estão disponíveis para atribuição ao produto configurável/agrupado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalada. A ID do patch é MDVA-41046. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 01229a69-c72a-4189-9be5-1761073b74ee
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-41046: produtos simples com opções personalizadas não disponíveis para atribuição

O patch MDVA-41046 resolve o problema em que produtos simples com opções personalizadas não estão disponíveis para atribuição ao produto configurável/agrupado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalada. A ID do patch é MDVA-41046. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Produtos simples com opções personalizadas não estão disponíveis para atribuição a produtos configuráveis/agrupados.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto simples com opções personalizáveis e defina um valor para o atributo configurável.
   * Use *Cor* como atributo configurável e selecione *Amarelo* como valor de cor.
1. Salve o produto simples.
1. Agora vá para a página criar produto configurável.
1. Percorra o assistente &quot;Criar configuração&quot; e certifique-se de selecionar *Amarelo* como a cor do atributo.
1. Sem salvar o produto configurável, selecione a opção &quot;Escolher produto diferente&quot; na lista suspensa Selecionar.
1. Isso abrirá uma grade de produtos filtrada pelo amarelo do atributo de cor. Agora selecione o produto simples que foi criado anteriormente com opções personalizáveis.
1. Salve o produto configurável.

<u>Resultados esperados</u>:

O produto simples com opções personalizadas está disponível para atribuição (visível na grade) na etapa 6.

<u>Resultados reais</u>:

A seção de configuração está vazia.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
