---
title: "MDVA-39713: O usuário pode editar a hora de início da atualização agendada ativa"
description: O patch MDVA-39713 corrige o problema em que um usuário pode editar a hora de início de uma atualização agendada ativa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-39713. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: c7221fdb-5fc0-4179-8d4c-c9e1f0d00692
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-39713: O usuário pode editar a hora de início da atualização agendada ativa

O patch MDVA-39713 corrige o problema em que um usuário pode editar a hora de início de uma atualização agendada ativa. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12 está instalada. A ID do patch é MDVA-39713. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.3.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário pode editar a hora de início de uma atualização agendada ativa.

<u>Etapas a serem reproduzidas</u>:

1. Criar novas páginas CMS.
1. Selecione **Agendar Nova Atualização** e defina a **Data de Início** como atual +1 minuto.
1. Ative a Atualização Agendada executando o comando `bin/magento cron:run --group=staging` no ambiente local. Aguarde alguns minutos e verifique se o agendamento está ativo.
1. Quando o agendamento estiver ativo, atualize a página.
1. Clique em **Exibir/Editar** na seção Alterações agendadas.
1. Edite o tempo adicionando +2 minutos e salve a alteração.
1. Salve a página do CMS.
1. Execute novamente o seguinte comando: `bin/magento cron:run --group=staging`.
1. Clique em **Exibir/Editar** da Atualização Agendada.

<u>Resultados esperados</u>:

O usuário não pode editar a hora de início de uma atualização agendada ativa.

<u>Resultados reais</u>:

O usuário recebe um erro como *Já existe um item (Magento\Cms\Model\Page) com a mesma ID &quot;11&quot;.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
