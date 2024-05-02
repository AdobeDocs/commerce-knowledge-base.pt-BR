---
title: "MDVA-43451: Erro ao definir Preço e Estrutura para catálogo compartilhado"
description: O patch MDVA-43451 resolve o problema em que o usuário não consegue definir a Precificação e a Estrutura de um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13 está instalada. A ID do patch é MDVA-43451. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
exl-id: 78de2e98-dfd7-4829-8e3f-76eadf5570e8
feature: Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# MDVA-43451: Erro ao definir Preço e Estrutura para catálogo compartilhado

O patch MDVA-43451 resolve o problema em que o usuário não consegue definir a Precificação e a Estrutura de um catálogo compartilhado. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.13 está instalado. A ID do patch é MDVA-43451. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário não pode definir preços e estrutura para um catálogo compartilhado. A seguinte mensagem é exibida: *O armazenamento solicitado não foi encontrado. Verifique o armazenamento e tente novamente.*

<u>Etapas a serem reproduzidas</u>:

1. Crie um site personalizado. As ids dos sites devem ser 0, 1, 2.
1. Crie uma loja no site acima. As ids dos armazenamentos devem ser 0,1,2.
1. Crie três exibições de loja para a loja acima. As IDs das exibições de loja devem ser 0,1, 2, 3, 4.
1. Exclua a exibição de loja com a id 2. Agora, a tabela de lojas deve ser semelhante à tabela abaixo.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. Crie um novo catálogo compartilhado.
1. Ao configurar Preço e Estrutura, selecione o armazenamento criado na Etapa 2.
1. Salve o catálogo compartilhado.

<u>Resultados esperados</u>:

O catálogo compartilhado é salvo sem nenhum problema.

<u>Resultados reais</u>:

Não é possível salvar o catálogo compartilhado. O seguinte erro é exibido:
*O armazenamento solicitado não foi encontrado. Verifique o armazenamento e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
