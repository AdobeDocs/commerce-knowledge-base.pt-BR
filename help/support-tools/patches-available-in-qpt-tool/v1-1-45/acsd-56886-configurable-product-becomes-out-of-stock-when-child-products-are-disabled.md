---
title: "ACSD-56886: o produto configurável fica indisponível quando os produtos secundários são desativados"
description: Aplique o patch ACSD-56886 para corrigir o problema do Adobe Commerce em que o produto configurável fica sem estoque quando os produtos são desativados.
feature: Products
role: Admin, Developer
exl-id: 809b9829-283f-4e3c-bf27-1944057f944f
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56886: o produto configurável fica indisponível quando os produtos secundários são desativados

O patch ACSD-56886 corrige o problema em que o produto configurável fica indisponível quando os produtos secundários são desativados. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45 está instalado. A ID do patch é ACSD-56886. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O produto configurável fica indisponível quando os produtos secundários são desativados.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon como Administrador.
1. Definir todos os indexadores no modo **[!UICONTROL Update By Schedule]**.
1. Crie o seguinte produto configurável:

   * Nome = *TESTE CONFIGURÁVEL 1*
   * Atributo = *cor*
   * Valores = *vermelho* e *preto*
   * Preço do produto filho **vermelho** = *$100*;
   * Preço do produto filho &quot;preto&quot; = *$200*.

1. Crie a seguinte atualização agendada para o produto configurável:

   * Data de Início = *3* minutos a partir de agora.
   * Data de Término = *5* minutos após a Data de Início.
   * Nome do produto = *TEST CONFIGURABLE 1 editado*.
   * Desabilite o produto filho **vermelho** na seção **Configurável**.

1. Aguarde a Data inicial.
1. Abra os detalhes do produto configuráveis na Loja.

<u>Resultados esperados</u>:

O produto configurável é exibido como **Em Estoque** com o rótulo **Tão baixo quanto 200**.

<u>Resultados reais</u>:

O produto configurável é exibido como **Sem Estoque**.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
