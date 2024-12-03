---
title: 'ACSD-53979: Ocorre um erro JS na página inicial'
description: Aplique o patch ACSD-53979 para corrigir o problema do Adobe Commerce em que ocorre um erro de JavaScript na página inicial se a mensagem de boas-vindas contiver uma aspa simples.
feature: Page Content
role: Admin, Developer
exl-id: 4e5afc5c-322f-4681-b2aa-01d93be74d4a
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-53979: Ocorre um erro do JavaScript na página inicial

O patch ACSD-53979 corrige o problema em que ocorre um erro de JavaScript na página inicial se a mensagem de boas-vindas contiver aspas simples. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.37 está instalado. A ID do patch é ACSD-53979. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro de JavaScript na página inicial se a mensagem de boas-vindas contiver uma aspa simples.

<u>Etapas a serem reproduzidas</u>:

1. Defina uma mensagem de boas-vindas padrão no arquivo `en_US.csv` no idioma [!DNL French] ou coloque um caractere de aspas como abaixo:
   `app/code/Magento/Theme/i18n/en_US.csv`

   ```CSV
       "Default welcome msg!","Message d'accueil par défaut"
   ```

1. Vá para o front-end.

<u>Resultados esperados</u>:

O front-end é carregado sem erros do JavaScript.

<u>Resultados reais</u>:

Ocorre um erro no JavaScript:

```JS
    Uncaught SyntaxError: Unable to process binding "ifnot: function(){return customer().fullname }"
    Message: Unable to parse bindings.
    Bindings value: text: 'Message d'accueil par défaut'
    Message: Unexpected identifier 'accueil'
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
