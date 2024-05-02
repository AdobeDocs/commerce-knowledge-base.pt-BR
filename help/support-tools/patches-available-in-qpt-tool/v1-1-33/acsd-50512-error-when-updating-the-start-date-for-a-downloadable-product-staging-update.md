---
title: "ACSD-50512: erro ao atualizar a data de início de uma atualização de preparo de produto baixável"
description: Aplique o patch ACSD-51892 para corrigir o problema de desempenho do Adobe Commerce em que o erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*; isso ocorre ao atualizar a data de início de uma atualização de preparo de produto para download.
feature: Products, Staging
role: Admin
exl-id: 873357ef-49c3-48f8-a98e-41c48cb9ba8b
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-50512: erro ao atualizar a data de início da atualização de preparo do produto baixável

O patch ACSD-50512 corrige o problema em que o erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*, ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.33 está instalado. A ID do patch é ACSD-51502. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*, ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável.

<u>Etapas a serem reproduzidas</u>:

1. Criar um produto baixável, com *links para download* e *links de exemplo*.
1. Crie uma atualização agendada para o mesmo produto e salve o produto.
1. Edite a atualização agendada pré-configurada (da etapa 2) e altere a data de início.
1. Salve a atualização programada.

<u>Resultados esperados</u>:

As alterações na atualização agendada foram salvas com êxito.

<u>Resultados reais</u>:

Você recebe o erro: *O link para download não está relacionado ao produto. Verifique o link e tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
