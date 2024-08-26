---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.50'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.50.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: f62cf4284d7bb99a1ab58df676dfff726c34d327
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.50

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.50.

O QPT v1.1.50 inclui os seguintes patches:

1. **ACSD-59280**: corrige o problema em que o erro *Chamada para método indefinido RefletionUnionType::getName()* ocorre ao instalar as versões 2.4.4-pX.
1. **ACSD-45049**: corrige o problema em que a configuração de atributo *[!UICONTROL Is required]* do cliente não funciona corretamente de acordo com o escopo do site no Administrador.
1. **ACSD-46938**: corrige o problema no desempenho da recriação de gatilhos de BD durante `setup:upgrade`.
1. **ACSD-48210**: corrige o problema em que a atualização do atributo *[!UICONTROL website scope]* em uma exibição de repositório específica substitui os valores de atributo no escopo global.
1. **ACSD-54887**: corrige o problema em que o carrinho de compras do cliente é limpo depois que a sessão do cliente expira com o *[!UICONTROL Persistent Shopping Cart]* habilitado.
1. **ACSD-58141**: corrige o problema em que `PHPSESSID` é regenerado em solicitações POST na área de vitrine para um cliente conectado se o [!UICONTROL L2 Redis cache] estiver habilitado e o cliente for atualizado pelo Administrador.
1. **ACSD-58352**: corrige o problema em que os rótulos de atributo de retorno para a exibição de repositório padrão são retornados por meio da API do GraphQL quando uma exibição de repositório não padrão é especificada no cabeçalho da solicitação.
1. **ACSD-58442**: corrige o problema em que dispositivos com uma largura de *768px* são tratados como dispositivos móveis, fazendo com que o menu e o cabeçalho sejam carregados em uma exibição móvel em vez de na área de trabalho.
1. **ACSD-58790**: corrige a funcionalidade *pinçar para zoom* nas imagens da página de detalhes do produto no modo de exibição móvel do [!DNL Chrome].
1. **ACSD-59036**: corrige uma exceção que ocorre ao carregar preços de produtos com limites inferiores e superiores iguais a *$0*.
1. **ACSD-59229**: corrige o problema em que as informações relacionadas ao grupo de clientes são salvas no segmento errado devido ao valor antigo de [!UICONTROL X-Magento-Vary] na solicitação.
1. **ACSD-59378**: corrige o problema em que substituições de URL de nível de repositório são atualizadas incorretamente durante a importação.
1. **ACSD-59514**: corrige o problema em que os formulários na área de Administração com [!DNL Page Builder] acionavam o *[!DNL Page Builder]por 5 segundos sem liberar bloqueios.* erro no console do navegador após o envio do formulário e as alterações não podem ser salvas.
1. **ACSD-60303**: corrige o problema em que um pedido do Administrador não pode ser feito se a minificação de HTML estiver habilitada.
1. **ACSD-60441**: corrige o problema com a atualização de clientes por meio do ponto de extremidade `V1/customers REST API` ao usar o token de acesso de integração gerado do back-end.

Use o menu à esquerda para navegar até uma página de patch específica.

