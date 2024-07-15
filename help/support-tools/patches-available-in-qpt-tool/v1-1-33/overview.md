---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: df3ae5e2-7c57-4ccd-af34-eb78cc60bcf6
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.33

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.33.

O QPT v1.1.33 inclui os seguintes patches:

1. **ACSD-50478**: corrige o comando de reversão de banco de dados para um caso em que o despejo de banco de dados contém disparadores e um comando SQL delimitador.
1. **ACSD-50512**: corrige o erro: *O link disponível para download não está relacionado ao produto. Verifique o link e tente novamente.* isso acontece ao atualizar a data de início de uma atualização de preparo de produto baixável.
1. **ACSD-50949**: corrige o problema em que o filtro de preço em [!UICONTROL Advanced Search] não retorna resultados adequados quando usado com o filtro SKU.
1. **ACSD-51645**: corrige o erro lançado ao salvar um novo [!UICONTROL Cart Price Rule] se a extensão `Magento_OfflineShipping` estiver desabilitada.
1. **ACSD-50895**: corrige o problema em que [!DNL Google Analytics] 3 marcas GTM não são acionadas se [!DNL Google Analytics] 4 GTM não estiver configurado.
1. **ACSD-51102**: corrige o problema em que uma regra de catálogo aplicada a um grande número de produtos não é indexada corretamente quando a regra é habilitada por uma atualização agendada.
1. **ACSD-50368**: corrige o problema em que o `group_id` do cliente é ignorado quando um cliente é criado por meio da API REST assíncrona ou da API REST em massa assíncrona.
1. **ACSD-51497**: corrige o problema em que um cliente não pode classificar uma página de catálogo por [!UICONTROL Custom Attribute] do tipo suspenso.
1. **ACSD-51408**: corrige o problema em que o status do item de pedido está incorretamente definido como [!UICONTROL Backordered].
1. **ACSD-51735**: corrige o problema em que o status do item do pedido é incorretamente definido como [!UICONTROL Ordered] quando o estoque de produtos é *0*.
1. **ACSD-51792**: corrige o problema em que uma página não tem o evento de impressão quando o [!DNL Google Tag Manager] 4 está habilitado.
1. **ACSD-51471**: corrige o problema em que um usuário administrador não pode salvar uma atualização agendada para um produto agrupado que usa um produto simples que tem uma atualização agendada.
1. **ACSD-51700**: corrige o erro que ocorre ao alternar exibições da loja em uma página de edição de produto baixável no administrador.
1. **ACSD-51120**: corrige o problema em que o cache de solicitações do GraphQL GET não é limpo para páginas CMS que contêm blocos CMS atualizados por meio de uma atualização de preparo.
1. **ACSD-51240**: corrige o problema em que o arquivo carregado está ausente se o registro for feito por meio do formulário de registro da empresa.
1. **ACSD-51907**: corrige o problema em que um usuário administrador restrito não pode criar um memorando de crédito com um reembolso offline.
1. **ACSD-52148**: corrige o problema em que o logon do [!UICONTROL Google V3 reCAPTCHA Admin] falha ocasionalmente.
1. **ACSD-51431**: corrige o problema em que o status de um indexador está funcionando, mesmo se não houver novas entradas no log de alterações.
1. **ACSD-51892**: corrige o problema de desempenho em que os arquivos de configuração são carregados várias vezes durante a implantação.

Use o menu à esquerda para navegar até uma página de patch específica.
