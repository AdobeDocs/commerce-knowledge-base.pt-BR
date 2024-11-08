---
title: "MDVA-38799: os produtos baixáveis não são salvos após a criação de uma atualização de preparo"
description: O patch MDVA-38799 resolve o problema em que os produtos baixáveis não são salvos após a criação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 está instalada. A ID do patch é MDVA-38799. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: 306f9ef3-ca3a-41b9-a5d3-42aa4ef59953
feature: Products, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# MDVA-38799: Produtos baixáveis não salvos após a criação de uma atualização de preparo

O patch MDVA-38799 resolve o problema em que os produtos baixáveis não são salvos após a criação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.0 está instalada. A ID do patch é MDVA-38799. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0-2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos baixáveis não são salvos após a criação de uma atualização de preparo. Os usuários recebem a mensagem de erro: *A amostra para download não está relacionada ao produto. Verifique o link e tente novamente*.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até **Catálogo** > **Produtos**.
1. Clique na lista suspensa ao lado de Adicionar produto e selecione Produto baixável.
   * Preencha o nome, SKU, preço e quantidade do produto.
1. Role para baixo até a página Informações baixáveis.
1. Em Amostras, clique em **Adicionar link**.
   * Preencha o Título, Fazer upload do arquivo (o tipo de arquivo não importa).
1. Clique em **Salvar**. Você receberá a seguinte mensagem: *Você salvou o produto*.
1. Clique em **Agendar nova atualização** na parte superior da página.
   * Preencha o Nome da atualização e uma Data de início e data de término válidas.
1. Clique em **Salvar** na atualização de preparo.
1. Clique em **Salvar** no produto.

<u>Resultados esperados</u>:

O produto é salvo sem erros.

<u>Resultados reais</u>:

Você recebe a mensagem de erro: *A amostra para download não está relacionada ao produto. Verifique o link e tente novamente*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
