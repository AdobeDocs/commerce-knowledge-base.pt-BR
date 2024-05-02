---
title: Remoção do acesso ao Blackfire para Adobe Commerce na infraestrutura em nuvem
description: Em 11 de abril de 2020, o acesso gratuito ao monitoramento de desempenho do Blackfire não será mais incluído nas assinaturas de arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Pro ou Adobe Commerce na infraestrutura em nuvem Starter.  Você não poderá mais fazer login em sua conta Blackfire. É possível continuar usando o Blackfire além de 11 de abril, comprando uma licença diretamente pelo Blackfire.io. Os comerciantes da Adobe Commerce que não tiverem comprado licenças diretamente do Blackfire até essa data terão suas licenças gratuitas do Blackfire fornecidas pelo Adobe desativadas. Além disso, a funcionalidade para criar novos relatórios usando a ferramenta Profiler será desativada. Ainda é possível que os clientes que usam a arquitetura Pro hospedada na infraestrutura em nuvem recebam monitoramento gratuito do desempenho da infraestrutura por meio do New Relic Infrastructure.
exl-id: bf33c2c6-e9b3-474a-a127-909b51dff92f
feature: Cloud, Paas
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# Remoção do acesso ao Blackfire para Adobe Commerce na infraestrutura em nuvem

Em 11 de abril de 2020, o acesso gratuito ao monitoramento de desempenho do Blackfire não será mais incluído nas assinaturas de arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Pro ou Adobe Commerce na infraestrutura em nuvem Starter.  Você não poderá mais fazer login em sua conta Blackfire. É possível continuar usando o Blackfire além de 11 de abril, comprando uma licença diretamente pelo Blackfire.io. Os comerciantes da Adobe Commerce que não tiverem comprado licenças diretamente do Blackfire até essa data terão suas licenças gratuitas do Blackfire fornecidas pelo Adobe desativadas. Além disso, a funcionalidade para criar novos relatórios usando a ferramenta Profiler será desativada. Ainda é possível que os clientes que usam a arquitetura Pro hospedada na infraestrutura em nuvem recebam monitoramento gratuito do desempenho da infraestrutura por meio do New Relic Infrastructure.

**Se quiser continuar usando o Blackfire**:

1. Você deve adquirir uma licença diretamente com o Blackfire.
1. Em seguida, configure o Blackfire usando esses [etapas](https://blackfire.io/docs/integrations/paas/magentocloud).
1. Se tiver dificuldades com a instalação, você poderá [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para solicitar assistência. Para perguntas específicas sobre Blackfire, entre em contato com o suporte de Blackfire diretamente em [support@blackfire.io](mailto:support@blackfire.io).

## Se você tiver erros ao executar uma implantação:

Se, ao executar uma implantação, você receber erros relacionados ao Blackfire, faça o seguinte:

1. Remova o Blackfire da sua configuração. Edite o `.magento.app.yaml` arquivar e remover o Blackfire da seção de tempo de execução:

   ```YAML
   ...
   # Enable extensions required by Magento 2
   runtime:
     extensions:
     - redis
     - xsl
     - json
     -**blackfire**
      - imap
   ...
   ```

1. Conclua isso no ambiente de desenvolvimento local e envie para a nuvem.

Somente [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) se você vir o seguinte erro depois de executar uma implantação:

*Aviso do PHP: Inicialização do PHP: não é possível carregar a biblioteca dinâmica &#39;blackfire.so&#39; (tentado: /usr/lib/php/20180731-zts/blackfire.so (/usr/lib/php/20180731-zts/blackfire.so: não é possível abrir o arquivo de objeto compartilhado: esse arquivo ou diretório não existe), /usr/lib/php/20180731-zts/blackfire.so.so (/usr/lib/php/20180731-zts/blackfire.so.so: não é possível abrir o arquivo de objeto compartilhado: esse arquivo ou diretório não existe) em Desconhecido na linha 0*

Este erro significa que o plug-in do Blackfire deve ser atualizado e impedido de carregar.

**Se quiser usar o New Relic Infrastructure**:

Para saber como acessar o New Relic Infrastructure, consulte [Acessar o New Relic](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) em nossa base de conhecimento de suporte.
