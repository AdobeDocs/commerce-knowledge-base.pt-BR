---
title: 'MDVA-42584: Status de estoque do produto configurável não atualizado automaticamente'
description: O patch MDVA-42584 resolve o problema em que o status do estoque do produto configurável não é atualizado automaticamente quando seu produto simples é atualizado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-42584. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: bf2697a2-8d15-408b-8d59-7b4173537e60
feature: Configuration, Orders, Products
role: Admin
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-42584: Status de estoque do produto configurável não atualizado automaticamente

O patch MDVA-42584 resolve o problema em que o status do estoque do produto configurável não é atualizado automaticamente quando seu produto simples é atualizado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-42584. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O status do estoque do produto configurável no back-end não é atualizado automaticamente quando seu produto simples é definido como **No Stock** por meio de API ou importação.

<u>Pré-requisitos</u>:

MSI instalado.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto configurável, **InvCheck001**, com duas opções: **InvCheck001-M** e **InvCheck001-L**.
1. Ambos os produtos simples devem ter Quantidade e devem estar **No Estoque** para que o produto configurável também esteja **No Estoque** no back-end.
1. Agora, atualize os produtos simples e defina Quantidade como **0** e Status do Estoque como **Sem Estoque**.
1. Atualize o produto configurável e verifique se o status do estoque foi atualizado para **Sem Estoque**.
1. Use o ponto de extremidade de API a seguir e defina o produto simples **InvCheck001-M** como **Em Estoque** com Quantidade > 0.

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

1. Vá para o back-end e verifique a quantidade e o status do estoque do produto simples **InvCheck001-M**. Foi atualizado para **Em estoque**.
1. Atualize o produto configurável e verifique o status do estoque.

<u>Resultados esperados</u>:

O status do estoque do produto configurável **InvCheck001** no back-end é atualizado automaticamente para **Em Estoque**.

<u>Resultados reais</u>:

O status do estoque do produto configurável ainda é **Sem Estoque**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
