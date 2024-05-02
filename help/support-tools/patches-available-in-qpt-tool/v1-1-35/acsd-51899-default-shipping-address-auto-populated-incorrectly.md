---
title: "ACSD-51899: endereço de entrega padrão preenchido automaticamente incorretamente"
description: Aplique o patch ACSD-51899 para corrigir o problema do Adobe Commerce em que o endereço de envio padrão é preenchido automaticamente com um endereço errado.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: endereço de entrega padrão preenchido automaticamente incorretamente

O patch ACSD-51899 corrige o problema em que o endereço de envio padrão é preenchido automaticamente com um endereço errado. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.35 está instalado. A ID do patch é ACSD-51899. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O endereço de entrega padrão é preenchido automaticamente com um endereço errado

<u>Etapas a serem reproduzidas</u>:

1. Ativar **Coleta na loja** em método de envio.
1. Criar *estoque* e *origem*.
1. Crie o produto e atribua-o à origem.
1. Adicionar um produto ao carrinho.
1. Clique em **Prosseguir para o check-out** do minicarrinho.
1. Insira o endereço de email de teste e selecione **Escolher na loja**.
1. Clique em **Selecionar armazenamento** e selecione um local de armazenamento para separação.
1. Clique no link **próximo** botão.
1. Navegue até a **Página inicial** clicando no logotipo da loja.
1. Abra o **Mini carrinho**.
1. Clique no hiperlink inferior chamado **Exibir e editar carrinho**.
1. Clique em **Prosseguir para o check-out**.
1. Clique no botão de envio na página de envio.

<u>Resultados esperados</u>

O campo de endereço de entrega permanece vazio, exceto por *País, região e código postal*.

<u>Resultados reais</u>

O endereço de entrega padrão é preenchido automaticamente com *Coleta na loja* após atualizar a página.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
