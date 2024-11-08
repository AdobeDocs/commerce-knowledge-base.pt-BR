---
title: "MDVA-39993: As alterações de inventário feitas por meio da API não são refletidas na loja"
description: O patch MDVA-39993 resolve o problema em que as alterações de inventário feitas por meio da API não são refletidas na loja. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-39993. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 2d49b9b7-8a70-44f3-80bf-4460bb2e61d5
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# MDVA-39993: As alterações de inventário feitas por meio da API não são refletidas na loja

O patch MDVA-39993 resolve o problema em que as alterações de inventário feitas por meio da API não são refletidas na loja. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-39993. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.5 - 2.3.7-p2 e 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As alterações de inventário feitas por meio da API não são refletidas na página do produto da loja.

<u>Pré-requisitos</u>:

Módulos de inventário instalados.

<u>Etapas a serem reproduzidas</u>:

1. Verifique se a fila está definida para execução com o cron e se o cron está instalado e em execução.
1. Crie um produto configurável (COC001), com duas cores (preto e vermelho) e dois tamanhos (M e L).
1. Faça uma opção em estoque (COC001-Red-M).
1. Carregue a página do produto configurável na vitrine e tente clicar em cada cor. Ao clicar em **Vermelho**, o tamanho **M** deve ser riscado porque está esgotado.
1. Faça o COC001-Red-M em estoque usando o seguinte endpoint de API e a carga:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Verifique esse produto simples no back-end e verifique se ele foi atualizado para Em estoque.
1. Carregue o produto configurável do front-end e clique em cada cor. Observe o tamanho **M** ao clicar em **Vermelho**.

<u>Resultados esperados</u>:

A opção COC001-Red-M não é riscada porque foi atualizada para Em estoque pela API.

<u>Resultados reais</u>:

A opção COC001-Red-M ainda está riscada, mesmo que esteja em estoque.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
