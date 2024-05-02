---
title: "ACSD-50817: otimiza o trabalho cron sales_clean_quotes para ser executado mais rápido"
description: Aplique o patch ACSD-50817 para otimizar o trabalho cron "sales_clean_quotes" para ser executado mais rápido adicionando um índice composto nas colunas "store_id" e "updated_at" na tabela de cotações.
exl-id: b08b12ff-37ac-4a7d-bce2-2a27e4f916f0
feature: Quotes
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-50817: Otimiza o trabalho cron `sales_clean_quotes` para executar mais rápido

O patch ACSD-50817 otimiza o trabalho cron `sales_clean_quotes` para executar mais rápido adicionando um índice composto no `store_id` e `updated_at` na tabela de cotações. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.31 está instalado. A ID do patch é ACSD-50817.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O trabalho cron `sales_clean_quotes` está muito lento. Com este patch, ele foi otimizado para ser executado mais rápido ao adicionar um índice composto no `store_id` e `updated_at` na tabela de cotações.

<u>Etapas a serem reproduzidas</u>:

1. Gerar 50 a 80 milhões de cotações com `updated_at` definido como &lt; período de 30 dias.
1. Execute a tarefa cron `sales_clean_quotes` ou na seguinte consulta na tabela de cotações:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Resultados esperados</u>

Trabalho Cron `sales_clean_quotes` é otimizado para ser executado mais rapidamente adicionando um índice composto no `store_id` e `updated_at` na tabela de cotações.

<u>Resultados reais</u>

A consulta está muito lenta.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
