---
title: 'ACSD-45241: quantidade de estoque do produto virtual calculada incorretamente'
description: O patch ACSD-45241 corrige o problema em que a quantidade em estoque do produto virtual é calculada incorretamente após a criação de um memorando de crédito. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-45241. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: quantidade de estoque do produto virtual calculada incorretamente

O patch ACSD-45241 corrige o problema em que a quantidade em estoque do produto virtual é calculada incorretamente após a criação de um memorando de crédito. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-45241. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A quantidade de estoque de um produto virtual é calculada incorretamente após a criação de um memorando de crédito.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável com um produto virtual como um produto secundário no Administrador do Commerce.
1. Certifique-se de que ambos os produtos criados na etapa um estejam em estoque.
1. Marque a quantidade do produto virtual criado na etapa um como 100 e mantenha a quantidade vendável como 100 também.
1. Adicione o produto ao carrinho de compras.
1. Faça um pedido com o produto virtual criado na primeira etapa.
1. Mantenha o status do pedido como &quot;Pendente&quot;. Não é necessário processar o pagamento.
1. Registro `order_created` criado em `inventory_reservation`. A quantidade do produto virtual mostra 100 com a quantidade vendável como 99.
1. Abra o pedido e vá para **Fatura** > **Enviar Fatura**.
1. Registro `invoice_created` criado em `inventory_reservation`. A quantidade virtual do produto agora é de 99, e a quantidade comercializável também é de 99.
1. Crie um memorando de crédito sem selecionar **Retornar ao Estoque**.

<u>Resultados esperados</u>:

Nenhum novo registro é criado em `inventory_reservation`, e a quantidade em estoque do produto virtual permanece inalterada.

<u>Resultados reais</u>:

Um registro `creditmemo_created` é criado em `inventory_reservation`, e a quantidade do estoque de produtos virtuais é ajustada para 98 com a quantidade vendável como 99.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
