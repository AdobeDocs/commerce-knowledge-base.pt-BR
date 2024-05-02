---
title: "ACSD-51120: o cache de solicitação do GraphQL GET não é limpo para páginas CMS que contêm blocos CMS"
description: Aplique o patch ACSD-51120 para corrigir o problema do Adobe Commerce em que o cache de solicitação do GraphQL GET não é limpo para páginas CMS que contêm blocos CMS.
exl-id: 22abba89-b697-45d7-972e-bf3233e5e9ec
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-51120: cache de solicitação do GraphQL GET não limpo para páginas CMS que contêm blocos CMS

O patch ACSD-51120 corrige o problema em que o cache de solicitação do GraphQL GET não é limpo para páginas CMS que contêm blocos CMS atualizados por meio de uma atualização de preparo. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.33 está instalado. A ID do patch é ACSD-51120. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cache de solicitação do GraphQL GET não é limpo para páginas CMS que contêm blocos CMS atualizados por meio de uma atualização de preparo.

<u>Etapas a serem reproduzidas</u>:

1. Crie um bloco CMS.
1. Inclua o bloco CMS em uma página CMS usando o [!DNL Page Builder].
1. Busque a página CMS usando a consulta do GraphQL fornecida usando uma solicitação GET:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Verifique se a resposta do GraphQL está armazenada em cache em [!DNL Varnish].
1. Crie uma atualização agendada para o bloco.
1. Aguarde a atualização programada ser aplicada e execute o trabalho cron para aplicar a atualização programada.
1. Busque a página CMS novamente usando a consulta do GraphQL fornecida usando uma solicitação GET.

<u>Resultados esperados</u>:

A resposta mostra o conteúdo atualizado.

<u>Resultados reais</u>:

A resposta ainda mostra o conteúdo antigo.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
