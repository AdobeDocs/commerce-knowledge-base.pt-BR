---
title: "E: Erro ao verificar route.yaml erro durante a implantação de preparo ou produção"
description: '"Este artigo fornece uma solução para o problema de infraestrutura em nuvem do Adobe Commerce, em que você recebe a mensagem de erro *"E: Erro ao verificar rotas.yaml"* ao tentar implantar o projeto no ambiente de preparo ou produção."'
exl-id: 7f58591a-5581-46cd-984d-09ac2c0f3903
feature: Deploy, Routes, Staging
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# E: Erro ao verificar o erro route.yaml durante a implantação de preparo ou produção

Este artigo fornece uma solução para o problema de infraestrutura na nuvem do Adobe Commerce, em que você recebe a mensagem de erro *&quot;E: Erro ao verificar rotas.yaml&quot;* ao tentar implantar o projeto no ambiente de preparo ou produção.

## Versões afetadas

* Adobe Commerce na infraestrutura em nuvem, todas as versões

## Problema

<u>Etapas a serem reproduzidas</u>:

Acione uma implantação enviando o código para o ambiente de preparo ou produção.

<u>Comportamento esperado</u>:

Implantação bem-sucedida.

<u>Comportamento real</u>:

A implantação está bloqueada e a seguinte mensagem de erro é exibida no log:

<pre>Implantação de aplicativos Verificação da configuração E: erro ao verificar route.yaml.
Os domínios a seguir estão configurados para o cluster, mas não têm rotas definidas no arquivo route.yaml:

- store1.example.com
- store2.example.com
- test-store.example.com

Com sua configuração atual route.yaml,
  esses domínios NÃO seriam atendidos!

Para continuar, consulte aqui para obter instruções sobre como solucionar problemas:
 /help/troubleshooting/deployment/e-error-verifying-routes-yaml-error-during-staging-or-production-deploy.md</pre>

## Causa

Este erro ocorre se a configuração de rota para quaisquer domínios adicionais que foram adicionados ao seu projeto estiverem ausentes do arquivo `routes.yaml`.

Como parte da atualização de habilitação de autoatendimento do Adobe Commerce para configuração de rota de autoatendimento, adicionamos uma verificação de pré-implantação para garantir que todos os domínios no seu projeto tenham rotas configuradas no arquivo `routes.yaml`. Se algum domínio não tiver configuração de rota, a implantação será bloqueada.

## Solução

Para resolver a implantação bloqueada, atualize o arquivo `routes.yaml` para configurar rotas para os domínios listados na mensagem de erro usando um dos seguintes métodos:

* Aplique o patch fornecido pelo Adobe Commerce durante o processo de atualização.
* Adicionar manualmente a configuração de rota ausente ao arquivo `routes.yaml`.

### Método 1: aplicar o patch fornecido pelo Adobe Commerce

1. Procure um tíquete de suporte recente da Adobe Commerce com o título &quot;*Habilitar recursos de autoatendimento para &lt;project\_ID>&quot;.*
1. Siga as instruções no tíquete para aplicar o patch, que atualiza a configuração de rota para o seu ambiente de nuvem.
1. СConfirme e envie as alterações para reimplantar seu projeto.

### Método 2: adicionar manualmente a configuração de rota ausente

1. Para servir todos os domínios em seu projeto usando a mesma configuração de rota, atualize o arquivo `routes.yaml` adicionando modelos de rota para o domínio padrão e todos os outros domínios em seu projeto, conforme mostrado no exemplo a seguir:

   ```yaml
   "http://{default}/":
       type: upstream
       upstream: "mymagento:http"
   "http://{all}/":
       type: upstream
       upstream: "mymagento:http"
   ```

1. СConfirme e envie suas alterações para reimplantar seu projeto.

Para obter instruções detalhadas sobre como atualizar a configuração de rota, consulte [Cloud para Adobe Commerce > Configurar rotas](https://devdocs.magento.com/guides/v2.3/cloud/project/project-conf-files_routes.html) na documentação do desenvolvedor.

>[!NOTE]
>
>Se a configuração do seu projeto especificar domínios que não estão mais em uso, conclua as seguintes etapas para removê-los do seu projeto o mais rápido possível: 1. Envie um tíquete de suporte com uma lista de domínios para remover dos ambientes do projeto. 2. Depois que a equipe de suporte remover os domínios, atualize o arquivo `routes.yaml` para remover todas as referências aos domínios obsoletos.
