---
title: "MDVA-34474: a atualização da lista de requisições de API resulta em erro"
description: O patch MDVA-34474 corrige o problema em que adicionar um produto à lista de requisições usando a API resulta em erro. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-34474. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: dc39c4f7-417c-45ea-914c-32f7305527da
feature: REST, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-34474: a atualização da lista de requisições da API resulta em erro

O patch MDVA-34474 corrige o problema em que adicionar um produto à lista de requisições usando a API resulta em erro. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-34474. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.0

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce no local e Adobe Commerce na infraestrutura em nuvem 2.3.0 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A adição de um produto à lista de requisições usando a API resulta em erro.

<u>Etapas a serem reproduzidas</u>:

1. Ativar lista de requisições no Administrador (**Lojas** > **Configuração** > **Geral** > **Recursos B2B** > **Habilitar Lista de Requisições** = *Sim*).
1. Crie um cliente.
1. Crie uma nova lista de requisições para este cliente enviando a chamada ```json    POST rest/all/V1/requisition_lists``` com a carga json anexada.

<u>Resultados esperados</u>:

Sem erros, e a lista é criada.

<u>Resultados reais</u>:

Erro 400.

```json
{"message":"Could not save Requisition List"}
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
