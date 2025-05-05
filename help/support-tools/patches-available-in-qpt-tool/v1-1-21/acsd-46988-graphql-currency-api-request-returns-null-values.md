---
title: 'ACSD-46988: a solicitação da API de moeda do GraphQL retorna valores nulos'
description: O patch ACSD-46988 corrige o problema em que a solicitação da API de moeda do GraphQL retorna valores nulos para uma moeda personalizada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalada. A ID do patch é ACSD-46988. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: a solicitação da API de moeda do GraphQL retorna valores nulos

O patch ACSD-46988 corrige o problema em que a solicitação da API de moeda do GraphQL retorna valores nulos para uma moeda personalizada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalado. A ID do patch é ACSD-46988. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A solicitação da API de moeda do GraphQL retorna valores nulos para uma moeda personalizada.

<u>Etapas a serem reproduzidas</u>:

1. Configure a moeda personalizada no Admin. Vá para **Sistema** > **Configuração** > **Geral** > **Configuração de Moeda**.
1. Envie uma solicitação do GraphQL com a seguinte carga:

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u>Resultados esperados</u>:

A solicitação retorna valores de moeda em vez de valores nulos.

<u>Resultados reais</u>:

A solicitação retorna vários valores nulos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Ferramentas de correção de qualidade > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia Ferramenta de correção de qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Etapas adicionais necessárias após a instalação do patch

Para usuários locais:

* Executar: `composer require symfony/intl:"~5.4.11"`

Para usuários da nuvem:

* Executar: `composer require symfony/intl:"~5.4.11"`
* Envie `composer.json` e `composer.lock` arquivos para o repositório Git junto com o arquivo de patch.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia Ferramenta de Patches de Qualidade.
