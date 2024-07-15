---
title: "Correção de comércio MC-41359: configurações ausentes Parâmetro de cookie SameSite"
description: O patch de comércio MC-41359 corrige o problema de configurações de parâmetros de cookies SameSite ausentes. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MC-41359. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: b48faa3f-0d9a-4d65-9abb-1573c6240635
feature: Observability
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Correção de comércio MC-41359: configurações ausentes Parâmetro de cookie SameSite

O patch de comércio MC-41359 corrige o problema de configurações de parâmetros de cookies SameSite ausentes. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MC-41359. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.4.2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce no local e Adobe Commerce na infraestrutura de nuvem 2.3.6-p1, 2.4.2, 2.4.2-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Configurações ausentes do parâmetro de cookie SameSite.

<u>Etapas a serem reproduzidas:</u>

Pré-requisitos:

* Abra o Chrome e acesse chrome://flags/
* Habilitar **Cookies SameSite por padrão** e **Cookies sem SameSite devem ser seguros**.
* Abra o Inspetor de Chrome.

<u>Cenário 1:</u>

1. Ative o PayPal.
1. Vá para a loja.
1. Adicione um produto ao carrinho.
1. Vá para o check-out.

<u>Cenário 2:</u>

Se você tiver o New Relic [habilitado](https://docs.magento.com/user-guide/reports/new-relic-reporting.html), o aviso será exibido em qualquer página de front-end.

<u>Resultado real:</u>

Mensagem de aviso no console do navegador: *Um cookie associado a um recurso entre sites foi definido sem um atributo SameSite.*

<u>Resultado esperado:</u>

&quot;lax&quot; não deve ser adicionado ao domínio do cookie; o atributo samesite deve estar presente com o valor padrão.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte [Patches disponíveis na ferramenta QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
