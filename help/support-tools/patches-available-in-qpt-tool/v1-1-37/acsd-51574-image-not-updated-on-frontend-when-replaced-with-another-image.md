---
title: "ACSD-51574: imagem não atualizada no front-end quando substituída por outra imagem"
description: Aplique o patch ACSD-51574 para corrigir o problema do Adobe Commerce em que a imagem não é atualizada no front-end depois de substituí-la por outra imagem.
feature: Configuration
role: Admin
exl-id: a6f26126-71c3-43c2-bba4-60a914d7ec11
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-51574: imagem não atualizada no front-end quando substituída por outra imagem

O patch ACSD-51574 corrige o problema em que a imagem não é atualizada no front-end depois de substituí-la por outra imagem. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.37 está instalado. A ID do patch é ACSD-51574. Observe que o problema foi corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A imagem não é atualizada no front-end depois de substituí-la por outra imagem.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com algumas imagens.
1. Edite o produto e carregue uma imagem com um nome conhecido (Exemplo: *image.jpg*).
1. Salve o produto.
1. Edite o produto novamente, exclua a versão antiga da imagem e faça upload da nova versão da imagem com o mesmo nome. **Verifique se a nova versão é visivelmente diferente para ver o problema.**
1. Salve o produto. O administrador e o front-end exibem as imagens.
1. Edite o produto novamente e faça upload novamente da mesma nova imagem (usando o mesmo nome).
1. Salve o produto e verifique a página do produto no front-end.

<u>Resultados esperados</u>:

A imagem carregada pela segunda vez deve ser a nova imagem, juntamente com o nome da imagem renomeada.

<u>Resultados reais</u>:

A imagem carregada pela segunda vez é a versão anterior excluída da imagem, em vez da mesma imagem nova.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
