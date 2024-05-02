---
title: "ACSD-52277: o usuário administrador redirecionou incorretamente ao selecionar a exibição da loja ao criar um novo pedido"
description: Aplique o patch ACSD-52277 para corrigir o problema do Adobe Commerce em que um usuário administrador não é redirecionado corretamente após selecionar a exibição da loja ao criar um novo pedido no Admin.
exl-id: 6f0b86ae-f6f1-44cf-aef5-64def5f14824
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-52277: o usuário administrador redirecionou incorretamente ao selecionar a exibição da loja ao criar um novo pedido

O patch ACSD-52277 corrige o problema em que um usuário administrador não é redirecionado corretamente após selecionar a exibição da loja ao criar um novo pedido no Admin. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.34 está instalado. A ID do patch é ACSD-52277. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4, 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um usuário administrador não é redirecionado corretamente após selecionar a exibição da loja ao criar um novo pedido.

<u>Etapas a serem reproduzidas</u>

1. Instale uma instância limpa.
1. Crie um produto.
1. Crie um site adicional, uma loja e duas visualizações de loja.
1. Criar um pedido do Administrador selecionando *exibição de loja 1*.

<u>Resultados esperados</u>:

O usuário é redirecionado para a página de pedido.

<u>Resultados reais</u>:

O usuário não é redirecionado para a página do pedido após selecionar a visualização de loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
