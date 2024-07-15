---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6170c616-312c-4de3-98dc-e2c27c376608
source-git-commit: 42712af2ce4337cd64b8dea555139e4252fb91cf
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.48

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.48.

O QPT v1.1.48 inclui os seguintes patches:

1. **ACSD-55566**: corrige o problema em que o *[!UICONTROL mergeCart mutation]* falha com um *Erro Interno do Servidor* na resposta do GraphQL ao mesclar carrinhos de origem e de destino que têm os mesmos itens agrupados.
1. **ACSD-56546**: corrige o problema em que os produtos configuráveis e agrupados são exibidos como *[!UICONTROL Out of Stock]* na loja quando a configuração *[!UICONTROL Display Out of Stock Product]* está desabilitada.
1. **ACSD-56635**: corrige o problema em que o cliente importado é duplicado com o mesmo endereço de email quando a importação é usada com [!UICONTROL Account Sharing] definido como *[!UICONTROL Global]*.
1. **ACSD-56741**: corrige a mensagem de erro *Tentando acessar o deslocamento da matriz no valor do tipo nulo* que é exibida durante `setup:upgrade` quando o banco de dados contém um gatilho MySQL personalizado não relacionado ao mecanismo de indexação e [!DNL MView].
1. **ACSD-57315**: corrige o problema em que uma nova transação é criada em [!DNL PayPal Payflow Pro] sempre que o botão **[!UICONTROL Fetch]** é clicado na tela exibir transação no [!UICONTROL Admin].
1. **ACSD-57337**: corrige o problema em que um usuário administrador com restrições de acesso a sites específicos pode ver empresas de todos os sites na grade *[!UICONTROL Companies]*.
1. **ACSD-57394**: corrige a classificação de produto incorreta por campos de classificação múltipla no GraphQL.
1. **ACSD-57565**: corrige o problema em que o painel *[!UICONTROL Order]* exibe informações de pedido incorretas até que o período seja atualizado. O painel agora exibe estatísticas de ordem corretas na primeira carga.
1. **ACSD-57854**: corrige o problema em que as solicitações de GraphQL de produto retornam categorias desabilitadas nas agregações de categoria.
1. **ACSD-58008**: corrige o problema em que a atualização programada remove a versão anterior do item preparado se nenhuma data final for especificada.

Use o menu à esquerda para navegar até uma página de patch específica.

