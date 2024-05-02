---
title: "ACSD-46988: a solicitação da API de moeda do GraphQL retorna valores nulos"
description: O patch ACSD-46988 corrige o problema em que a solicitação da API de moeda do GraphQL retorna valores nulos para uma moeda personalizada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalada. A ID do patch é ACSD-46988. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
exl-id: 8da0ab99-8db9-4222-9400-6df1520267f0
feature: REST, GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-46988: a solicitação da API de moeda do GraphQL retorna valores nulos

O patch ACSD-46988 corrige o problema em que a solicitação da API de moeda do GraphQL retorna valores nulos para uma moeda personalizada. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.21 está instalado. A ID do patch é ACSD-46988. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A solicitação da API de moeda do GraphQL retorna valores nulos para uma moeda personalizada.

<u>Etapas a serem reproduzidas</u>:

1. Configure a moeda personalizada no Admin. Ir para **Sistema** > **Configuração** > **Geral** > **Configuração de moeda**.
1. Envie uma solicitação do GraphQL com a seguinte carga:

<pre>
<code class="language-graphql">
{
    currency {
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates {
            currency_to
            rate
        }
    }
}
</code>
</pre>

<u>Resultados esperados</u>:

A solicitação retorna valores de moeda em vez de valores nulos.

<u>Resultados reais</u>:

A solicitação retorna vários valores nulos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Ferramentas de correção de qualidade > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) na guia Ferramenta de correções de qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Etapas adicionais necessárias após a instalação do patch

Para usuários locais:

* Executar: `composer require symfony/intl:"~5.4.11"`

Para usuários da nuvem:

* Executar: `composer require symfony/intl:"~5.4.11"`
* Push `composer.json` e `composer.lock` para o repositório Git junto com o arquivo de patch.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na guia Ferramenta de correções de qualidade.
