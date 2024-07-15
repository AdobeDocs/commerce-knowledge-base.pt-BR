---
title: "Correção MDVA-13203: erro 503 homepage post full reindex"
description: '"O patch do MDVA-13203 Adobe Commerce corrige o problema em que seu site está mostrando uma página de manutenção e há *CRITICAL: SQLSTATE\[23000\]: erros de violação de restrição de integridade* no `system.log`. A ID do patch é MDVA-13203. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada.'''
exl-id: 8e09010b-9aa4-4a79-b546-a24bb72e0e40
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Correção MDVA-13203: erro 503 homepage postar reindexação completa

O patch MDVA-13203 do Adobe Commerce corrige o problema em que seu site está mostrando uma página de manutenção e há *CRÍTICO: SQLSTATE\[23000\]: Violação de restrição de integridade* erros no `system.log`. A ID do patch é MDVA-13203. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura de nuvem 2.2.4.

**Compatível com as versões do Adobe Commerce:** Adobe Commerce (todos os métodos de implantação) 2.3.0-2.4.1.

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas:</u>

1. Vá para o URL afetado.
1. Você verá a página de manutenção.
1. Verifique se o site não está em status de manutenção por meio do SSH:
   <pre> manutenção do bin/magento:status
    Status: o modo de manutenção não está ativo
    Lista de endereços IP isentos: nenhum</pre>
1. Examinar `system.log`:

<pre>grep critical -i var/log/system.log |tail

[2018-09-04 17:05:18] report.CRITICAL: SQLSTATE[23000]: Violação de restrição de integridade: 1062 Entrada duplicada '4613' para a chave 'PRIMARY', a consulta era: INSERT INTO `search_tmp_5b8ebb4e994da5_88027289` (`entity_id`,`score`) VALORES (?, ?),... (?, ?), (?, ?) [] []
[2018-09-04 17:05:21] report.CRITICAL: SQLSTATE[23000]: Violação de restrição de integridade: 1062 Entrada duplicada '4613' para a chave 'PRIMARY', a consulta era: INSERT INTO `search_tmp_5b8ebb51579943_5233638` ( VALORES (?, ?),...,(?, ?) DE`entity_id`,`score`) [] []
[2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Violação de restrição de integridade: 1062 Entrada duplicada '1350' para a chave 'PRIMARY', a consulta era: INSERT INTO `search_tmp_5b8ebb6b7028f4_68065024` (`entity_id`,`pontuação`) VALORES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []
[2018-09-04 17:05:47] report.CRITICAL: SQLSTATE[23000]: Violação de restrição de integridade: 1062 Entrada duplicada '1350' para a chave 'PRIMARY', a consulta era: INSERT INTO `search_tmp_5b8ebb6b7885a9_23360993` (`entity_id`,`pontuação`) VALORES (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?), (?, ?) [] []

data

Ter Set 4 17:06:11 UTC 2018</pre>

<u>Resultados esperados:</u> você deve ver o site.

<u>Resultados reais:</u> a página de manutenção é exibida devido a problemas de consistência do banco de dados.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
