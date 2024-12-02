---
title: Implantação paralisada com o erro "Não é possível fazer upload do aplicativo para o cluster remoto"
description: 'Este artigo fornece uma solução para o problema do Adobe Commerce, em que a implantação trava, e a seguinte mensagem de erro pode ser encontrada no log de implantação: *"Erro: não é possível carregar o aplicativo para o cluster remoto"*.'
exl-id: 30f0ec31-db27-429c-b065-cf7770a72194
feature: Deploy
role: Developer
source-git-commit: 8b6bf1cdada7edb0cdb0bb3e90ed15ee8cebf77e
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Implantação paralisada com o erro &quot;Não é possível fazer upload do aplicativo para o cluster remoto&quot;

Este artigo fornece uma solução para o problema do Adobe Commerce, em que a implantação trava, e a seguinte mensagem de erro pode ser encontrada no log de implantação: *&quot;Erro: não é possível carregar o aplicativo para o cluster remoto&quot;*.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

<u>Etapas a serem reproduzidas</u>:

Acione a implantação manualmente ou executando uma mesclagem, push ou sincronização do seu ambiente.

<u>Resultado esperado</u>:

A implantação foi concluída com êxito.

<u>Resultado real</u>:

A implantação trava e, no log de erros de implantação na interface da nuvem, a seguinte mensagem de erro é exibida: *&quot;Erro: não é possível carregar o aplicativo para o cluster remoto&quot;, encontrado no log de implantação após falha na implantação, o site pode exibir o erro &quot;Tempo limite de 503 primeiros bytes&quot;*.

## Causa

O problema é causado pela paralisação do armazenamento disponível.

## Solução

Você pode considerar limpar os diretórios de log e/ou aumentar o espaço em disco.

Diretórios que devem ser considerados para limpeza:

* `var/log`
* `var/report`
* `var/debug/`
* `var`

Para obter detalhes sobre como aumentar o espaço em disco se você estiver na arquitetura de plano inicial do Adobe Commerce na infraestrutura de nuvem, consulte [Aumentar espaço em disco para o ambiente de integração na nuvem](/help/how-to/general/increase-disk-space-for-integration-environment-on-cloud.md) em nossa base de dados de conhecimento de suporte. As mesmas instruções podem ser usadas para aumentar o espaço do ambiente de integração da arquitetura de plano Pro da infraestrutura de nuvem do Adobe Commerce. Para produção/preparo profissional, você precisa [registrar um tíquete para o Suporte da Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket-Submit-a-support-ticket) e solicitar mais espaço em disco. Mas normalmente, você não precisará lidar com isso no ambiente de Preparo/Produção do plano Pro, pois o Adobe Commerce monitora esses parâmetros para você e alerta e/ou executa ações de acordo com o contrato.
