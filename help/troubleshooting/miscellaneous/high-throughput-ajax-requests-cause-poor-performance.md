---
title: Solicitações de AJAX de alta taxa de transferência causam baixo desempenho
description: Este artigo fornece uma solução para problemas de desempenho com o Adobe Commerce no local ou o Adobe Commerce em sites de infraestrutura em nuvem devido a algumas solicitações de alta taxa de transferência que causam carga e tráfego significativos no servidor.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Solicitações de AJAX de alta taxa de transferência causam baixo desempenho

Este artigo fornece uma solução para problemas de desempenho com o Adobe Commerce no local ou o Adobe Commerce em sites de infraestrutura em nuvem devido a algumas solicitações de alta taxa de transferência que causam carga e tráfego significativos no servidor.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Adobe Commerce no local 2.2.x, 2.3.x

>[!NOTE]
>
>O problema foi corrigido na versão 2.3.4 do Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local.

### Problema

O site enfrenta um desempenho lento devido a solicitações de alta taxa de transferência, como solicitações críticas de AJAX.

### Causa

As solicitações de AJAX de alta taxa de transferência incluem aquelas relacionadas ao conteúdo privado dos clientes.

### Solução

Há três soluções:

* [Atualizar para a versão 2.3.4](https://devdocs.magento.com/cloud/project/project-upgrade.html). Se isso não for possível no momento, [instalar o patch corrigindo o problema](/help/troubleshooting/known-issues-patches-attached/performance-issues-caused-by-excessive-ajax-requests.md).
* Garanta solicitações mais leves (solicitações de cache ou migração para conteúdo privado dos clientes).
* Reduza o número de solicitações.

<u>Garantir solicitações mais leves (solicitações de cache ou mover para o conteúdo privado dos clientes)</u>

Se houver solicitações de AJAX de terceiros acionadas em cada página, tente armazenar essas solicitações em cache ou movê-las para o conteúdo privado dos clientes. O comerciante pode fazer isso certificando-se de que as solicitações personalizadas de AJAX sejam chamadas usando os métodos HTTP do GET. Ele tornará essas solicitações armazenáveis em cache pelo Fastly. Se houver solicitações personalizadas de AJAX que não devem ser armazenadas em cache, elas devem ser refatoradas de acordo com a funcionalidade de conteúdo privado. Para obter etapas, consulte [Conteúdo privado](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html) na documentação do desenvolvedor.

<u>Reduzir o número de solicitações</u>

* Desative o carrinho de compras persistente, pois isso pode aumentar o número de `customer/section/load` solicitações. Siga as etapas em [Caminhos do carrinho de compras persistentes](https://devdocs.magento.com/guides/v2.3/config-guide/prod/config-reference-most.html#persistent-shopping-cart-paths) na documentação do desenvolvedor para ver se o carrinho de compras persistentes está ativado.
* Se precisar recarregar ou invalidar o conteúdo no `sections.xml` siga as etapas em [Conteúdo privado: invalidar conteúdo privado](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html#invalidate-private-content) na documentação do desenvolvedor. Certifique-se de que você não esteja usando o `customerData.reload()` método diretamente nas suas personalizações.
* Verifique outras solicitações de AJAX POST na mesma página. Abra a ferramenta de desenvolvedor do Google Chrome no navegador Google Chrome. Clique no link **Rede** e depois a guia **XHR** e haverá a lista de todas as solicitações de AJAX da página específica. Em seguida, clique em cada solicitação e, no campo Método de solicitação, devem estar as solicitações do GET. Observação: o Google Chrome é usado como exemplo, e também é possível fazer isso em outros navegadores.
* Verifique a funcionalidade do Google Tag Manager (GTM), que é uma solicitação de AJAX específica. O usuário pode remover esse AJAX e refatorar sua personalização com funcionalidade privada para reduzir o número total de solicitações para o servidor.
* Verifique se o banner do Adobe Commerce está ativado, mas não é usado. Talvez seja necessário [Desative a saída do banner do Adobe Commerce para melhorar o desempenho do site](/help/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.md).

### Leitura relacionada

Para obter mais informações sobre o conteúdo de clientes particulares, consulte [Conteúdo privado](https://devdocs.magento.com/guides/v2.3/extension-dev-guide/cache/page-caching/private-content.html?itm_source=devdocs&amp;itm_medium=search_page&amp;itm_campaign=federated_search&amp;itm_term=ajax%20requests) na documentação do desenvolvedor.
