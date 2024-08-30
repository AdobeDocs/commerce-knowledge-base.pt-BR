---
title: "ACSD-59229: erro de alocação de dados do grupo do cliente devido a um valor X-Magento-Vary desatualizado"
description: Aplique o patch ACSD-59229 para corrigir o problema do Adobe Commerce em que as informações relacionadas ao grupo de clientes são salvas no segmento errado devido a um valor X-Magento-Vary desatualizado na solicitação.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
source-git-commit: 41d502a85a0cbb4eb8d186e4c1e1256aec3f8740
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-59229: erro de alocação de dados do grupo do cliente devido a um valor X-Magento-Vary desatualizado

O patch ACSD-59229 corrige o problema em que as informações relacionadas ao grupo de clientes são salvas no segmento errado devido a um valor X-Magento-Vary desatualizado na solicitação. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.50 está instalado. A ID do patch é ACSD-59229. Observe que o problema foi corrigido na versão 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As informações relacionadas ao grupo do cliente são salvas no segmento errado devido a um valor X-Magento-Vary desatualizado na solicitação.

<u>Pré-requisitos</u>:

Verifique se o Adobe Commerce B2B com dados de exemplo está instalado e se [!DNL Varnish] está configurado.

<u>Etapas a serem reproduzidas</u>:

1. Configurar preços avançados para o [!DNL SKU 24-MB01]:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Atacado* = *$200*
      * *Varejista* = *$30*

1. Crie duas contas de cliente.
1. Atribua ambos os clientes ao grupo **Atacado**.
1. Abra duas sessões diferentes do navegador e faça logon com cada cliente.
1. Navegue até a página do produto **[!UICONTROL 24-MB01]** para cada cliente e verifique se o preço exibido é *$200*.
1. Altere o grupo de clientes de um dos clientes para **Varejo**.
1. Limpe o cache usando o comando: `bin/magento cache:flush full_page`.
1. Atualize a página do produto de cada cliente.

<u>Resultados esperados</u>:

1. O cliente de varejo pode ver o preço correto de *$30* para o produto.
1. O cliente no atacado pode ver o preço correto do produto em *$200*.

<u>Resultados reais</u>:

1. O cliente de varejo pode ver o preço correto de *$30* para o produto.
1. O cliente grossista vê um preço incorreto de *$30* (preço de varejo) para o produto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
