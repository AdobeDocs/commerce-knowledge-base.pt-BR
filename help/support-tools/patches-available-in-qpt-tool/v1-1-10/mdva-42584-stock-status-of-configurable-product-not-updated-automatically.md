---
title: "MDVA-42584: status do estoque do produto configurável não atualizado automaticamente"
description: O patch MDVA-42584 resolve o problema em que o status do estoque do produto configurável não é atualizado automaticamente quando seu produto simples é atualizado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-42584. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: Status de estoque do produto configurável não atualizado automaticamente

O patch MDVA-42584 resolve o problema em que o status do estoque do produto configurável não é atualizado automaticamente quando seu produto simples é atualizado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.10 está instalado. A ID do patch é MDVA-42584. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do estoque do produto configurável no back-end não é atualizado automaticamente quando seu produto simples é definido como **Em estoque** por meio da API ou importação.

<u>Pré-requisitos</u>:

MSI instalado.

<u>Etapas a serem reproduzidas</u>:

1. Criar um produto configurável, **InvCheck001**, com duas opções: **InvCheck001-M** e **InvCheck001-L**.
1. Ambos os produtos simples devem ter Quantidade e devem ser **Em estoque** para que o produto configurável também seja **Em estoque** no back-end.
1. Agora, atualize os produtos simples e defina a Quantidade como **0** e Status do Estoque para **Sem estoque**.
1. Atualize o produto configurável e verifique se o status do estoque foi atualizado para **Sem estoque**.
1. Use o endpoint de API a seguir e defina o produto simples **InvCheck001-M** para **Em estoque** com Quantidade > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Acesse o back-end e verifique a quantidade e o status do estoque do produto simples **InvCheck001-M**. É atualizado para **Em estoque**.
1. Atualize o produto configurável e verifique o status do estoque.

<u>Resultados esperados</u>:

O status do estoque do produto configurável **InvCheck001** no backend é atualizado automaticamente para **Em estoque**.

<u>Resultados reais</u>:

O status do estoque do produto configurável ainda é **Sem estoque**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
