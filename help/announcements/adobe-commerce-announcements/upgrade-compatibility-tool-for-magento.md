---
title: Ferramenta de compatibilidade de atualização 1.1.0 para Adobe Commerce
description: A Ferramenta de compatibilidade de atualização 1.1.0 é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos e o código principal instalados nela. Ele retorna uma lista de erros críticos, problemas e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce.
exl-id: 312abc5a-1d6a-4f32-9929-a94f4962eddd
feature: Upgrade
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Ferramenta de compatibilidade de atualização 1.1.0 para Adobe Commerce

A Ferramenta de compatibilidade de atualização 1.1.0 é uma ferramenta de linha de comando que verifica uma instância personalizada do Adobe Commerce em relação a uma versão específica, analisando todos os módulos e o código principal instalados nela. Ele retorna uma lista de erros críticos, problemas e avisos que devem ser abordados antes da atualização para a versão mais recente do Adobe Commerce.

## Quais são as novidades do UCT 1.1.0?

A Ferramenta de compatibilidade de atualização 1.1.0 apresenta melhorias significativas, incluindo:

* **Validar as modificações principais do arquivo**: a Adobe recomenda não personalizar o código dos produtos principais. Com esta versão, adicionamos um ponto de verificação para clientes e parceiros identificarem quaisquer modificações no código principal para entender o impacto das modificações antecipadamente e rapidamente. A inclusão dessa ferramenta no processo de desenvolvimento ajudará parceiros e comerciantes a identificar problemas de forma proativa, evitando problemas durante atualizações futuras e reduzindo o Custo Total de Propriedade (TCO).
* **Exportar o relatório para um arquivo JSON**: essa melhoria foi implementada após o feedback da comunidade. Agora, ao executar a ferramenta, os detalhes de todos os problemas identificados são exportados para um arquivo JSON para que os usuários possam ler, compartilhar e gerenciar os resultados sem precisar executar a ferramenta novamente.
* **Validações de VBE aprimoradas**: as VBEs (Vendor Bundled Extensions) não fazem parte do código principal do Adobe Commerce, mas são testadas e compatíveis com o Adobe. Com essa atualização, agora validamos VBEs usando a mesma abordagem que usamos para o código principal. Essa melhoria ajudará os usuários a entender claramente os problemas relacionados às personalizações e ao código principal/VBEs.
* **Fornecer códigos de erro**: introduzimos códigos de erro para ajudar os usuários a identificar, entender e resolver problemas durante uma atualização. As mensagens de erro e de aviso fornecem uma descrição clara e a solução sugerida.
* **Possibilidade de listar apenas problemas críticos**: com isso, os usuários poderão se concentrar apenas nos problemas críticos e que gerarão problemas durante a atualização.
* **Problemas de Delta entre duas versões**: com essa melhoria proposta pelos membros da comunidade, os usuários da UCT poderão obter uma discriminação dos problemas entre duas versões, o que permitirá que eles se concentrem apenas nos novos problemas introduzidos para a versão de destino que atualizarão.

## Quais versões a ferramenta pode comparar?

É possível usar a ferramenta para comparar qualquer versão 2.x.

## Quem pode usar a Ferramenta de compatibilidade de atualização 1.1.0?

Clientes do Adobe Commerce.

## Instale a Ferramenta de Compatibilidade de Atualização 1.1.0

Para obter as etapas de instalação, consulte Adobe Commerce: [Ferramenta de compatibilidade de atualização > Instalar](https://devdocs.magento.com/upgrade-compatibility-tool/install.html) na documentação do desenvolvedor. Para obter os pré-requisitos de uso da ferramenta, consulte Adobe Commerce: [Ferramenta de compatibilidade de atualização](https://devdocs.magento.com/upgrade-compatibility-tool/prerequisites.html) na documentação do desenvolvedor.

## Qual é o número ao lado de cada problema?

Esta é a referência da mensagem de erro que fornece informações sobre erros que podem ocorrer ao executar a Ferramenta de compatibilidade de atualização.

As mensagens de erro da Ferramenta de compatibilidade de atualização são categorizadas por nível (problemas críticos, erros e avisos) e tipo (código principal, código personalizado e esquemas do GraphQL). Cada tipo contém as seguintes informações:

* Código de erro: o identificador atribuído pelo Adobe Commerce para a mensagem de erro.
* Descrição do erro: uma descrição que resume a causa do erro.
* Ação sugerida pelo erro: se aplicável, fornece orientação para solucionar e resolver o erro.
* Os códigos estão listados e descritos no [Página de referência da mensagem de erro](https://devdocs.magento.com/upgrade-compatibility-tool/errors.html).

## Onde posso compartilhar feedback sobre a ferramenta?

Você pode entrar em contato com a equipe da UCT em nosso [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F) canal do slack. Estamos ansiosos para receber seus comentários e sugestões para melhorar a ferramenta.

## Leitura relacionada

* Blog da Adobe Commerce: [Introdução à Ferramenta de compatibilidade de atualização (Alpha)](https://magento.com/blog/magento-news/introducing-upgrade-compatibility-tool)
* Adobe Commerce: [Ferramenta de compatibilidade de atualização](https://devdocs.magento.com/upgrade-compatibility-tool/introduction.html) na documentação do desenvolvedor.
