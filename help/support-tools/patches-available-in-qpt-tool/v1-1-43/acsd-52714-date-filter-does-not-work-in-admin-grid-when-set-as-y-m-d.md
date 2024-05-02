---
title: "ACSD-52714: o filtro de data não funciona na grade do administrador quando definido como y-m-d"
description: Aplique o patch ACSD-52714 para corrigir o problema do Adobe Commerce em que o filtro de data não funciona na grade de administração quando o formato de data é definido como y-m-d.
feature: Attributes
role: Admin, Developer
exl-id: b292ab2c-e12d-40df-a9ad-19f25fbde5a0
source-git-commit: 513cb47c054dbb907810bbdc3d20d2aca9d5e42b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-52714: o filtro de data não funciona na grade de administração quando definido como y-m-d

O patch ACSD-52714 corrige o problema em que o filtro de data não funciona na grade do administrador quando o formato de data é definido como y-m-d. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.43 está instalado. A ID do patch é ACSD-52714. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O filtro de datas não funciona na grade de administração quando o formato de data é definido como y-m-d.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce limpo.
1. Editar
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
arquivo e adicionar
   `<dateFormat>Y-MM-dd</dateFormat>`
para
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
na tag
   `<dataType>date</dataType>`

1. Liberar o cache `bin/magento c:f`.
1. Faça logon no Administrador e crie um novo cliente em **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * de: data atual menos 1 dia
   * para: data atual

1. Clique em **[!UICONTROL Apply Filters]**.

<u>Resultados esperados</u>:

O filtro de data da grade funciona corretamente, independentemente do conjunto de localidades.

<u>Resultados reais</u>:

A seguinte mensagem é exibida: *Não foi possível encontrar nenhum registro*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
