---
title: "MDVA-43731: Os sinônimos de pesquisa não funcionam quando o valor é adicionado em 'Termos mínimos para correspondência'"
description: O patch MDVA-43731 corrige o problema em que os Sinônimos de pesquisa param de funcionar quando um valor é adicionado em "Termos mínimos para correspondência". Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-43731. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: b795989c-d10b-443e-aebe-f3859930396a
feature: Cache, Marketing Tools, Search
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-43731: Os sinônimos de pesquisa não funcionam quando o valor é adicionado em &quot;Termos mínimos para correspondência&quot;

O patch MDVA-43731 corrige o problema em que os Sinônimos de pesquisa param de funcionar quando um valor é adicionado em &quot;Termos mínimos para correspondência&quot;. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-43731. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os Sinônimos de pesquisa param de funcionar quando um valor é adicionado em &quot;Termos mínimos para correspondência&quot;.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com dados de amostra.
1. Configure o Elasticsearch7 como mecanismo de pesquisa.
1. Procure a palavra &quot;Jaqueta&quot;. Uma lista de produtos será exibida.
1. Adicione o parâmetro [4&lt;60%] em **Configuração** > **Catálogo** > **Pesquisa no Catálogo** > **Termos Mínimos para Correspondência**.
1. Limpe o cache de configuração e faça uma reindexação.
1. Pesquise novamente a palavra &quot;Jacket&quot; e observe que uma lista de produtos é exibida.
1. Vá para **Marketing** > **SEO e Pesquisa** > **Pesquisar Sinônimos**.
1. Crie Sinônimos de Pesquisa adicionando os seguintes sinônimos: jaqueta, bagtecs, express plus.
1. Faça uma reindexação.
1. Faça uma pesquisa de produto usando qualquer um dos sinônimos. Por exemplo, jaqueta.

<u>Resultados esperados</u>:

Você obtém a mesma lista de produtos de antes nos resultados da pesquisa.

<u>Resultados reais</u>:

Nenhum produto é mostrado nos resultados da pesquisa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
