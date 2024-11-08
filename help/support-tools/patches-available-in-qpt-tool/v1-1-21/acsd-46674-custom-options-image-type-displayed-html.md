---
title: "ACSD-46674: opções personalizadas do tipo de imagem exibido como HTML nos emails do cliente"
description: Aplique o patch ACSD-46674 para corrigir o problema do Adobe Commerce, em que as opções personalizadas do tipo de imagem são exibidas como HTML nos emails do cliente.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: opções personalizadas do tipo de imagem exibidas como HTML nos emails do cliente

O patch ACSD-46674 corrige o problema em que as opções personalizadas de um tipo de imagem são exibidas como HTML nos emails do cliente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21 está instalado. A ID do patch é ACSD-46674. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As opções personalizadas de um tipo de imagem são exibidas como HTML nos emails do cliente.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com uma opção personalizada.
   * Tipo de opção: *Arquivo*
   * Extensões de arquivo compatíveis: *png, jpg, gif*
   * Obrigatório: *Sim*
1. Faça um pedido deste produto usando uma imagem carregada como opção personalizada.
1. Crie uma fatura para o pedido criado na etapa dois.
1. Crie um memorando de crédito.
1. Verifique todos os emails de confirmação.

<u>Resultados esperados</u>:

Os emails de confirmação exibem a imagem carregada.

<u>Resultados reais</u>:

Os emails de confirmação contêm código de HTML simples em vez da imagem da opção personalizada do produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tools] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis em [!DNL QPT], consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
