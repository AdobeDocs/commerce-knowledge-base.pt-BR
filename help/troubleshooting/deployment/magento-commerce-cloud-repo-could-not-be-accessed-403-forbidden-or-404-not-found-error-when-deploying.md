---
title: "O Adobe Commerce no repositório de nuvem não pôde ser acessado: erro 403 Proibido ou 404 Não encontrado ao implantar"
description: "Este artigo discute como resolver o erro de implantação com falha do Adobe Commerce na infraestrutura em nuvem, semelhante ao seguinte:"
exl-id: 2f72d80a-05b2-4908-8fa8-61d06885ed07
feature: Cloud, Deploy, Paas, Variables
role: Developer
source-git-commit: 9ca95444aa785191e4c8bf1603773f3430414797
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# O Adobe Commerce no repositório de nuvem não pôde ser acessado: erro 403 proibido ou 404 não encontrado ao implantar

Este artigo discute como resolver o erro de implantação com falha do Adobe Commerce na infraestrutura em nuvem, semelhante ao seguinte:

&quot;*A URL &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; não pôde ser acessada: HTTP/1.1 403 Proibido* &quot;. Ou o arquivo &quot;*https://repo.magento.com/archives/magento/module-customer-segment/magento-module-customer-segment-102.0.5.0-patch2.zip&quot; não pôde ser baixado (HTTP/1.1 404 Não encontrado)*&quot;.

## Produtos e versões afetados

* Adobe Commerce na infraestrutura em nuvem 2.2.x, 2.3.x e 2.4.x

## Problema

Mensagem de erro na implantação indicando que a URL do repositório não pôde ser acessada.

<u>Etapas a serem reproduzidas</u>

Acione a implantação manualmente ou executando uma mesclagem, push ou sincronização do seu ambiente.

<u>Resultado real</u>

A implantação pára. No log de erros de implantação na interface do Project, uma mensagem de erro semelhante à seguinte é exibida:

*&quot;A URL &#39;https://repo.magento.com/archives/magento/magento-cloud-configuration/magento-magento-cloud-configuration-x.x.x.x.zip&#39; não pôde ser acessada: HTTP/1.1 \[403 Proibido ou 404 Não Encontrado\]&quot;*.

(Clique no ícone &quot;Falha&quot; na interface do usuário do projeto para ver o log.)

<u>Resultado esperado</u>

A implantação foi concluída com êxito.

## Causa

O erro é causado por chaves de autorização (chaves de acesso) inválidas, não especificadas ou não especificadas corretamente.

Alguns motivos para chaves não serem válidas são:

* Você gerou as chaves usando sua conta compartilhada.
* Sua licença foi revogada anteriormente devido a problemas de pagamento.

>[!NOTE]
>
>Se você perceber que isso se deve a um problema de faturamento ou de contrato expirado, entre em contato com a equipe de conta da Adobe para obter orientação para resolver esse problema. Depois que sua licença for reativada, seus direitos de suporte e implantação serão restaurados.

## Solução

Siga as etapas a seguir para resolver o problema com as chaves de autorização (consulte as seções abaixo para obter mais detalhes sobre cada etapa):

1. Obter as chaves de autorização válidas (ignore se tiver certeza de que a chave é válida).
1. Adicione o valor keys na variável `env:COMPOSER_AUTH` (ou verifique se o valor correto está lá) e verifique se as chaves são especificadas consistentemente na variável no nível do projeto e no nível do ambiente, bem como no arquivo `auth.json` (se existir) na raiz do projeto.
1. Atualize ou exclua `auth.json` para ter um único local onde a chave esteja configurada, se os valores das chaves de autorização não forem especificados ou tiverem outro valor.

### 1. Obter chaves de autorização válidas

Se você estava usando as chaves criadas na conta compartilhada, é necessário entrar em contato com o proprietário da licença da Adobe Commerce que fornece acesso e solicitar que ele gere as chaves para você.

Se sua licença tiver sido revogada anteriormente devido a problemas de pagamento e você tiver resolvido esses problemas e sua licença tiver sido renovada, será necessário [gerar as novas chaves de autenticação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html).

### 2. Adicione o valor keys na variável env:COMPOSER\_AUTH e verifique se as mesmas chaves são especificadas em auth.json

Consulte as instruções e informações relacionadas em [Preparar o sistema existente](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#auth-json) e [Adicionar chaves de autenticação](https://devdocs.magento.com/cloud/setup/first-time-setup-import-prepare.html#add-authentication-keys) na documentação do desenvolvedor.

### 3. Atualizar ou excluir auth.json

Veja a seguir uma descrição passo a passo de como atualizar suas chaves de autorização:

1. Faça logon no computador que tem suas chaves SSH do Adobe Commerce na infraestrutura em nuvem.
1. Faça logon no seu projeto: `magento-cloud login`
1. Crie uma ramificação para atualizar o código (no exemplo a seguir, o nome da ramificação é `auth` é criado a partir da ramificação primária):     `magento-cloud environment:branch auth master`
1. Mude para o diretório raiz do projeto.
1. Opcional: exclua o `auth.json` se preferir e continue para a [etapa 9](#step9).
1. Abra `auth.json` em um editor de texto.

   ```json
              {
                "http-basic":  {
                    "repo.magento.com": {
                        "username": "<public_key>",
                        "password": "<private_key>"
                        }
                      }
                    }
   ```

1. Adicione as chaves de autenticação corretas.
1. Salve as alterações e saia do editor de texto.
1. Confirmar e mesclar suas alterações:

   `git add -A`

   `git commit -m "<message>"`

   `git push origin master`
1. Aguarde a implantação do projeto.
