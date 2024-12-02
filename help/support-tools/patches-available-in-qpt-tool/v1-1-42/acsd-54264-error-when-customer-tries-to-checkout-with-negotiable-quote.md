---
title: 'ACSD-54264: erro quando o cliente tenta fazer check-out com a cotação negociável'
description: Aplique o patch ACSD-54264 para corrigir o problema do Adobe Commerce em que uma mensagem de erro "Você não pode atualizar o atributo solicitado. A linha ID:store_id" aparece quando um cliente tenta fazer check-out com uma cotação negociável de outra visualização de loja.
feature: B2B, Checkout
role: Admin, Developer
exl-id: de8f451e-3b0a-4721-9ff4-18553477db1d
source-git-commit: 2e344b1ca4bc075bdbc9074bb431a398f0871698
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-54264: o erro aparece quando o cliente tenta fazer check-out com a cotação negociável

O patch ACSD-54264 corrige o problema em que uma mensagem de erro *Você não pode atualizar o atributo solicitado. A ID da linha: store_id* aparece quando um cliente tenta fazer check-out com uma cotação negociável de outra exibição de loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.42 está instalado. A ID do patch é ACSD-54264. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Mensagem de erro *Não é possível atualizar o atributo solicitado. A ID da linha: store_id* aparece quando um cliente tenta fazer check-out com uma cotação negociável de outra exibição de loja.

<u>Pré-requisitos</u>:

Os módulos B2B do Adobe Commerce são instalados e ativados.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma exibição de loja adicional para o site padrão.
1. Habilite o *[!UICONTROL B2B Quote]* na configuração.
1. Faça logon como cliente da empresa em uma das visualizações da loja.
1. Adicione um produto ao *[!UICONTROL Shopping Cart]*.
1. Enviar a cotação para revisão.
1. Como um usuário administrador, vá para **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** e envie a cotação aprovada.
1. Como cliente da empresa, altere a exibição da loja para outra exibição de loja.
1. Tente verificar.

<u>Resultados esperados</u>:

O cliente faz um pedido com essa cotação.

<u>Resultados reais</u>:

* O erro ocorre ao salvar as informações de envio:

  `You cannot update the request attribute. Row ID: store_id =#`

* O seguinte erro é registrado:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
