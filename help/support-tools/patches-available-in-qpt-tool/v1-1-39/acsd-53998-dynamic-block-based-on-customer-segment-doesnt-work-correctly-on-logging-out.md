---
title: "ACSD-53998: Bloco dinâmico baseado em segmento de cliente funciona incorretamente após o logout"
description: Aplique o patch ACSD-53998 para corrigir o problema do Adobe Commerce em que um bloco dinâmico baseado em um segmento de cliente não funciona corretamente depois de fazer logout de uma conta de cliente.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
exl-id: 5a82a6b8-e8f7-47ff-89f6-93a39b72fe38
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# ACSD-53998: Bloco dinâmico baseado em segmento de cliente funciona incorretamente após o logout

O patch ACSD-53998 corrige o problema em que um bloco dinâmico baseado em um segmento de cliente não funciona corretamente depois de fazer logout de uma conta de cliente. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.39 está instalado. A ID do patch é ACSD-53998. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um bloco dinâmico baseado em um segmento de cliente não funciona corretamente depois de fazer logout de uma conta de cliente.

<u>Pré-requisitos</u>:

Instalar e habilitar [!DNL Page Builder] módulos.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois segmentos de clientes sem nenhuma condição.
1. Crie dois blocos dinâmicos para cada segmento.
1. Crie um bloco incluindo os dois blocos dinâmicos como [!DNL Page Builder] blocos dinâmicos.
1. Crie um widget incluindo o bloco acima e torne o bloco visível na seção de rodapé de todas as páginas.
1. Limpe os caches.
1. Abra a home page.
1. Faça logon como cliente.
1. Faça logout.

<u>Resultados esperados</u>:

O banner criado para clientes conectados não é exibido para usuários convidados.

<u>Resultados reais</u>:

O banner criado para o segmento de cliente conectado é exibido mesmo depois de fazer logout da conta do cliente.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
