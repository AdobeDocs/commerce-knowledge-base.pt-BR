---
title: Solicitações AJAX de alta taxa de transferência causam baixo desempenho
description: Este artigo fornece uma solução para problemas de desempenho com o Adobe Commerce no local ou o Adobe Commerce em sites de infraestrutura em nuvem devido a algumas solicitações de alta taxa de transferência que causam carga e tráfego significativos no servidor.
exl-id: 68dfca8a-826c-4476-acaf-a139052b5dcc
feature: Cache
role: Developer
source-git-commit: b6e44e106dcc546949459a79c0f2e49b87e1d376
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Solicitações AJAX de alta taxa de transferência causam baixo desempenho

Este artigo fornece uma solução para problemas de desempenho com o Adobe Commerce no local ou o Adobe Commerce em sites de infraestrutura em nuvem devido a algumas solicitações de alta taxa de transferência que causam carga e tráfego significativos no servidor.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x
* Adobe Commerce no local 2.2.x, 2.3.x

>[!NOTE]
>
>O problema foi corrigido na versão 2.3.4 do Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local.

### Problema

O site enfrenta um desempenho lento devido a solicitações de alta taxa de transferência, como solicitações críticas do AJAX.

### Causa

As solicitações de AJAX de alta taxa de transferência incluem aquelas relacionadas ao conteúdo privado dos clientes.

### Solução

Há três soluções:

* [Atualize para a versão 2.3.4](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version).
* Garanta solicitações mais leves (solicitações de cache ou migração para conteúdo privado dos clientes).
* Reduza o número de solicitações.

<u>Garanta solicitações mais leves (solicitações de cache ou mover para o conteúdo particular dos clientes)</u>

Se houver solicitações do AJAX de terceiros acionadas em cada página, tente armazenar essas solicitações em cache ou movê-las para o conteúdo privado dos clientes. O comerciante pode fazer isso certificando-se de que as solicitações personalizadas do AJAX sejam chamadas usando os métodos HTTP do GET. Ele tornará essas solicitações armazenáveis em cache pelo Fastly. Se houver solicitações personalizadas do AJAX que não devem ser armazenadas em cache, elas deverão ser refatoradas de acordo com a funcionalidade de conteúdo privado. Para ver as etapas, consulte [Conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) na documentação do desenvolvedor.

<u>Reduzir o número de solicitações</u>

* Desative o carrinho de compras persistente, pois isso pode aumentar o número de solicitações `customer/section/load`. Siga as etapas em [Caminhos de carrinho de compras persistentes](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/paths/config-reference-general) na documentação do desenvolvedor para ver se o carrinho de compras persistente está habilitado.
* Se você precisar recarregar ou invalidar o conteúdo no `sections.xml`, siga as etapas em [Conteúdo privado: Invalidar conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content) na documentação do desenvolvedor. Certifique-se de que você não esteja usando o método `customerData.reload()` diretamente em suas personalizações.
* Verifique outras solicitações POST AJAX na mesma página. Abra a ferramenta de desenvolvedor do Google Chrome no navegador Google Chrome. Clique na guia **Rede** e depois na guia **XHR**, e haverá a lista de todas as solicitações do AJAX da página específica. Em seguida, clique em cada solicitação e, no campo Método de solicitação, devem estar as solicitações do GET. Observação: o Google Chrome é usado como exemplo, e é possível fazer isso em outros navegadores também.
* Verifique a funcionalidade do Google Tag Manager (GTM), que é uma solicitação específica do AJAX. O usuário pode remover esse AJAX e refatorar sua personalização com funcionalidade privada para reduzir o número total de solicitações para o servidor.
* Verifique se o banner do Adobe Commerce está ativado, mas não é usado. Talvez seja necessário [Desabilitar a saída do banner do Adobe Commerce para melhorar o desempenho do site](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909).

### Leitura relacionada

Para obter mais informações sobre conteúdo privado de clientes, consulte [Conteúdo privado](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) na documentação do desenvolvedor.
