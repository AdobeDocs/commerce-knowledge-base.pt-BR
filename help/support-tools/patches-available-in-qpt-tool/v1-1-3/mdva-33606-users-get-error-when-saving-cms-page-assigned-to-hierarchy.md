---
title: "MDVA-33606: Os usuários recebem erro ao salvar a página CMS atribuída à hierarquia"
description: O patch MDVA-33606 resolve o problema em que os usuários obtêm o erro *Violação de restrição exclusiva encontrada* ao salvar uma página CMS atribuída à árvore de hierarquia. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3 está instalada. A ID do patch é MDVA-33606. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: Os usuários recebem um erro ao salvar a página CMS atribuída à hierarquia

O patch MDVA-33606 resolve o problema em que os usuários obtêm *Violação de restrição exclusiva encontrada* erro ao salvar uma página CMS atribuída à árvore hierárquica. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.3 está instalado. A ID do patch é MDVA-33606. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao tentar salvar uma página CMS atribuída à árvore hierárquica, os usuários recebem a seguinte mensagem de erro: *Violação de restrição exclusiva encontrada*.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova página CMS. Defina o escopo como Todos os modos de exibição de armazenamento. Esta é a sua página 1 do CMS.
1. Criar uma nova exibição de loja. Esta é a Visualização 2 da Loja.
1. Ir para **Conteúdo** > **Hierarquia** > Adicione a Página 1 do CMS à árvore hierárquica.
1. Altere o escopo para Exibição de armazenamento 2.
   * Desmarque &quot;Usar a hierarquia do nó principal&quot;.
   * Adicione a Página 1 do CMS a este escopo e salve-a.
1. Agora altere o escopo para Exibição de armazenamento padrão.
   * Desmarque &quot;Usar a hierarquia do nó principal&quot;.
   * Adicione a Página 1 do CMS a este escopo e salve-a.
1. Ir para **Conteúdo** > **Páginas** > **Adicionar nova página**.
   * Coloque o título da página como Page 2.
   * Na seção Página em Sites, atribua a Todas as exibições da loja e as exibições da loja (Exibição da loja padrão e Exibição da loja 2) e clique em **Salvar página**.
1. Na página de edição do CMS, abra a guia Hierarquia.
   * Atribua a Página 2 ao nó Exibição de armazenamento 2, nó Padrão e nó Todos os sites.

<u>Resultados esperados</u>:

Você pode atribuir a página CMS aos três nós sem qualquer erro.

<u>Resultados reais</u>:

Você recebe o seguinte erro: *Violação de restrição exclusiva encontrada*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
