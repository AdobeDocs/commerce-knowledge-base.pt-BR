---
title: 'ACSD-56760: o usuário administrador está restrito a um site específico e não pode classificar ou adicionar novos produtos'
description: Aplique o patch ACSD-56760 para corrigir o problema do Adobe Commerce em que o usuário administrador, que está restrito a um site específico e não pode classificar ou adicionar novos produtos dentro de uma categoria, caso a loja da Web tenha sua própria categoria raiz.
role: Admin
exl-id: fc1898ce-dcd7-4c0b-bef0-445219e8455f
source-git-commit: a8e1b3b5b9de41c62bf819ef68ac9f89626483a1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-56760: o usuário administrador está restrito a um site específico e não pode classificar ou adicionar novos produtos

O patch ACSD-56760 corrige o problema em que o usuário administrador, que está restrito a um site específico e não pode classificar ou adicionar novos produtos dentro de uma categoria, caso a loja da Web tenha sua própria categoria raiz. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.47 está instalado. A ID do patch é ACSD-56760. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador que está restrito a um site específico e não pode classificar ou adicionar novos produtos dentro de uma categoria caso a loja da Web tenha sua própria categoria raiz.

<u>Etapas a serem reproduzidas</u>:

1. Criar *2* sites.
1. Criar um **[!UICONTROL restricted admin user]** com acesso somente a *1* site.
1. Faça logon como o **[!UICONTROL restricted admin user]** e tente alterar as posições dos produtos em uma categoria.

*Caso 1*:

* *2* lojas.
* *2* categorias raiz, cada site atribuído a sua própria raiz de categoria.

*Caso 2*:

* *2* lojas.
* Apenas a categoria raiz *1* está atribuída aos dois sites.

<u>Resultados esperados</u>:

* *Caso 1*: o administrador restrito deve ser capaz de classificar produtos dentro da categoria disponível.
* *Caso 2*: o administrador restrito não pode classificar produtos dentro da categoria disponível, pois isso também afetará o armazenamento restrito.

<u>Resultados reais</u>:

* *Caso 1*: o administrador restrito não pode classificar produtos dentro da categoria disponível.
* *Caso 2*: o administrador restrito pode classificar produtos dentro da categoria disponível, afetando as lojas restritas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
