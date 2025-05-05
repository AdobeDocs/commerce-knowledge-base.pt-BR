---
title: 'ACSD-50512: erro ao atualizar a data de início de uma atualização de preparo de produto baixável'
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

O patch ACSD-50512 corrige o problema em que o erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*, que ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51502. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O erro *O link para download não está relacionado ao produto. Verifique o link e tente novamente*, que ocorre ao atualizar a data de início de uma atualização de preparo de produto baixável.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto para download, com *links para download* e *links de exemplo*.
1. Crie uma atualização agendada para o mesmo produto e salve o produto.
1. Edite a atualização agendada pré-configurada (da etapa 2) e altere a data de início.
1. Salve a atualização programada.

<u>Resultados esperados</u>:

As alterações na atualização agendada foram salvas com êxito.

<u>Resultados reais</u>:

Você recebe o erro: *O link para download não está relacionado ao produto. Verifique o link e tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
