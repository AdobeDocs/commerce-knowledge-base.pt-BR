---
title: "ACSD-48448: emissão de condição de corrida durante cancelamentos de pedidos, causando entrada duplicada na tabela inventory_reservation"
description: Aplique o patch ACSD-48448 para corrigir o problema de desempenho do Adobe Commerce em que o problema de condição de corrida ocorre durante os cancelamentos de pedidos, o que causa entradas duplicadas na tabela inventory_reservation.
feature: Orders, Checkout
role: Admin
exl-id: 69d00219-bc9f-4531-9e85-38476c2258ed
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48448: problema de condição *[!UICONTROL Race]* durante cancelamentos de pedidos, causando entrada duplicada na tabela `inventory_reservation`

O patch ACSD-48448 corrige o problema em que a condição *[!UICONTROL Race]* ocorre durante cancelamentos de pedidos, o que causa entradas duplicadas na tabela `inventory_reservation`. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.34 está instalado. A ID do patch é ACSD-48448. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p2 e 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O problema de condição *[!UICONTROL Race]* ocorre durante cancelamentos de pedidos, o que causa entradas duplicadas na tabela `inventory_reservation`.

<u>Etapas a serem reproduzidas</u>:

1. Fazer um pedido.
1. Verifique a tabela `inventory_reservation` para verificar se há um registro para o evento `order_placed`.
1. Execute o script anexado para cancelar o pedido em paralelo (lembre-se de alterar o URL e orderID).

`bash cancel_order.sh`

```
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Resultados esperados</u>:

Os registros não são duplicados.

<u>Resultados reais</u>:

Registros duplicados são criados na tabela `inventory_reservation` para `order_canceled`.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
