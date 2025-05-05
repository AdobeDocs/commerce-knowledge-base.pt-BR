---
title: 'ACSD-52831: Não é possível colocar ordens de cotação negociáveis quando [!DNL Google reCAPTCHA v3 Invisible] habilitado'
description: Aplique o patch ACSD-52831 para corrigir o problema do Adobe Commerce em que você não pode fazer pedidos de cotação negociáveis quando o  [!DNL Google reCAPTCHA v3 Invisible]  está habilitado.
feature: Quotes, B2B, Checkout
role: Admin
exl-id: 80cf5592-0784-4b37-8373-abec0847a9f0
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52831: Não é possível colocar ordens de cotação negociáveis quando [!DNL Google reCAPTCHA v3 Invisible] está habilitado

O patch ACSD-52831 corrige o problema em que você não consegue fazer pedidos de cota negociáveis quando [!DNL Google reCAPTCHA v3 Invisible] está habilitado. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.35 está instalado. A ID do patch é ACSD-52831. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Não é possível colocar ordens de cotação negociáveis quando [!DNL Google reCAPTCHA v3 Invisible] está habilitado.

<u>Etapas a serem reproduzidas</u>:

1. Ative o recurso Citação B2B.
1. Habilite [!DNL Google reCAPTCHA v3 Invisible] na loja para habilitar check-out/pedidos de colocação.
1. Gerar uma cotação e prosseguir para o check-out com essa cotação.
1. Você não poderá fazer um pedido devido ao erro CAPTCHA.

<u>Resultados esperados</u>:

A cotação continua até o check-out.

<u>Resultados reais</u>:

Você recebeu o erro *Falha na validação do reCAPTCHA. Tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
