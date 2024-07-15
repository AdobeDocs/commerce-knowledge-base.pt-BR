---
title: "ACSD-49389: pronto para recebimento de email enviado pela API quando não estiver pronto para recebimento"
description: Aplique o patch ACSD-49389 para corrigir o problema do Adobe Commerce em que um email pronto para recebimento é enviado pela API quando o pedido não está pronto para recebimento.
exl-id: a1baae06-cf36-448b-bda4-aff1e5ca68db
feature: REST, Communications
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-49389: pronto para recebimento de email enviado pela API quando não estiver pronto para recebimento

O patch ACSD-49389 corrige o problema em que um email pronto para coleta é enviado pela API quando o pedido não está pronto para coleta. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29 está instalado. A ID do patch é ACSD-49389. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [página de aterrissagem do QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um email pronto para coleta é enviado pela API quando o pedido não está pronto para coleta.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar o método *[!UICONTROL In-Store Delivery]*.
1. Criar uma origem de estoque com localização de retirada habilitada.
1. Crie um novo estoque usando o site principal com a fonte criada acima.
1. Crie um produto atribuindo a mesma origem.
1. Definir quantidade em estoque = 1.
1. Confira o produto criado na etapa 4 usando o método *[!UICONTROL In-Store Delivery]* na loja.
1. Criar uma fatura para o pedido.
1. Defina a quantidade do produto como *0* e tire-o do estoque.
1. O Post faz a seguinte solicitação de API:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Resultados esperados</u>:

O email Pronto para retirada não é enviado.

<u>Resultados reais</u>:

A API retorna *A ordem não está pronta para retirada*, mas o email pronto para retirada foi enviado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
