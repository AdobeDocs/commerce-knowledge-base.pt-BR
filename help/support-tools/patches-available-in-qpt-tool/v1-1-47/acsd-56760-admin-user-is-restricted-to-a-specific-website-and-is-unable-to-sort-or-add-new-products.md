---
title: "ACSD-56760: o usuário administrador está restrito a um site específico e não pode classificar ou adicionar novos produtos"
description: Aplique o patch ACSD-56760 para corrigir o problema do Adobe Commerce em que o usuário administrador, que está restrito a um site específico e não pode classificar ou adicionar novos produtos dentro de uma categoria, caso a loja da Web tenha sua própria categoria raiz.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: o usuário administrador está restrito a um site específico e não pode classificar ou adicionar novos produtos

O patch ACSD-56760 corrige o problema em que o usuário administrador, que está restrito a um site específico e não pode classificar ou adicionar novos produtos dentro de uma categoria, caso a loja da Web tenha sua própria categoria raiz. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.47 está instalado. A ID do patch é ACSD-56760. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador que está restrito a um site específico e não pode classificar ou adicionar novos produtos dentro de uma categoria caso a loja da Web tenha sua própria categoria raiz.

<u>Etapas a serem reproduzidas</u>:

1. Criar *2* Web sites.
1. Criar um **[!UICONTROL restricted admin user]** com acesso somente a *1* site.
1. Faça logon como **[!UICONTROL restricted admin user]** e tente alterar as posições do produto em uma categoria.

*Caso 1*:

* *2* lojas.
* *2* categorias raiz, cada site atribuído a sua própria raiz de categoria.

*Caso 2*:

* *2* lojas.
* Somente *1* a categoria raiz é atribuída a ambos os sites.

<u>Resultados esperados</u>:

* *Caso 1*: o administrador restrito deve ser capaz de classificar os produtos dentro da categoria disponível.
* *Caso 2*: o administrador restrito não pode classificar produtos dentro da categoria disponível, pois isso também afetará o armazenamento restrito.

<u>Resultados reais</u>:

* *Caso 1*: o administrador restrito não pode classificar produtos dentro da categoria disponível.
* *Caso 2*: o administrador restrito pode classificar produtos dentro da categoria disponível, afetando as lojas restritas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
