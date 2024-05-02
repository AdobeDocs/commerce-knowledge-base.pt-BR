---
title: "ACSD-51853: os estilos de texto copiados não são aplicados usando o construtor de páginas"
description: Aplique o patch ACSD-51853 para corrigir o problema do Adobe Commerce em que os estilos de texto copiados não são aplicados quando o Page Builder é usado.
feature: Page Builder
role: Admin
exl-id: 1efd3147-1ae0-468b-af04-1632fbaaefda
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-51853: Estilos de texto copiados não são aplicados usando o construtor de página

O patch ACSD-51853 corrige o problema em que os estilos de texto copiados não são aplicados quando o Page Builder é usado. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.34 está instalado. A ID do patch é ACSD-51853. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Estilos de texto copiados não são aplicados quando o Page Builder é usado

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Admin.
1. Acesse > **conteúdo** > **páginas** > **Abrir qualquer página** > **Editar com o Page Builder**.
1. Arraste a linha e *Texto* de **[!UICONTROL Elements]**.
1. Copiar **conteúdo enriquecido**, cole esse texto em uma **[!UICONTROL Page Builder]**.

<u>Resultados esperados</u>

O texto copiado é colado com todos os estilos.

<u>Resultados reais</u>

O texto copiado é colado como texto sem formatação e todos os estilos são perdidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
