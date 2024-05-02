---
title: "ACSD-46520: status de pedido incorreto quando reembolsado usando créditos da loja"
description: Este artigo fornece uma solução para o problema em que os usuários obtêm um status de pedido incorreto quando reembolsados usando créditos da loja.
exl-id: 8464df22-0223-4ded-a15f-ce06eacdf77c
feature: Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46520: status de pedido incorreto quando reembolsado usando créditos de loja

O patch ACSD-46520 resolve o problema em que os usuários obtêm um status de pedido incorreto quando reembolsados usando créditos da loja. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.20 está instalado. A ID do patch é ACSD-46520. Observe que o problema foi corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 e 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários obtêm um status de pedido incorreto quando reembolsados usando créditos da loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente na loja e faça logon.
1. Atribua créditos da loja ao cliente do Administrador. Os créditos da loja devem cobrir toda a ordem.
1. Fazer um pedido usando os créditos da loja.
1. Faturar a ordem.
1. Crie um aviso de crédito para reembolsar o valor total da ordem.
Selecione o **[!UICONTROL Refund to store credit]** caixa de seleção
1. Verifique o status do pedido.

<u>Resultados esperados</u>:

O status do pedido é *Fechado*.

<u>Resultados reais</u>:

O status do pedido é *Concluído*, que não é o status correto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou [!DNL Magento Open Source] no local: [Ferramentas de correção de qualidade > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) na guia Ferramenta de correções de qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na guia Ferramenta de correções de qualidade.
