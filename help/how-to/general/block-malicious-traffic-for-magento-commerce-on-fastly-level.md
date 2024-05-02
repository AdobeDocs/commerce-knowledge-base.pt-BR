---
title: Bloquear tráfego mal-intencionado para o Adobe Commerce no nível Fastly
description: Este artigo fornece as etapas que você pode seguir para bloquear tráfego mal-intencionado quando suspeitar que o Adobe Commerce na loja de infraestrutura na nuvem está enfrentando um ataque de DDoS.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Bloquear tráfego mal-intencionado para o Adobe Commerce no nível Fastly

Este artigo fornece as etapas que você pode seguir para bloquear tráfego mal-intencionado quando suspeitar que o Adobe Commerce na loja de infraestrutura na nuvem está enfrentando um ataque de DDoS.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.3.x

Neste artigo, pressupomos que você já tenha os IPs mal-intencionados e/ou seu país e agentes do usuário. Normalmente, os usuários do Adobe Commerce na infraestrutura em nuvem obteriam essas informações do suporte da Adobe Commerce. As seções a seguir fornecem etapas para bloquear o tráfego com base nessas informações. Todas as alterações devem ser feitas no ambiente de Produção.

## Obter acesso ao Painel de administração

Se o seu site for sobrecarregado pelo DDoS, talvez você não consiga fazer logon no Commerce Admin (e executar todas as etapas descritas mais adiante neste artigo).

Para obter acesso ao Administrador, coloque o site no modo de manutenção, conforme descrito em [Ativar ou desativar modo de manutenção](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html#instgde-cli-maint) e inclua seu endereço IP na lista de permissões. Desative o modo de manutenção depois que isso for concluído.

## Bloquear tráfego por IP

Para o Adobe Commerce no armazenamento de infraestrutura em nuvem, a maneira mais eficiente de bloquear o tráfego por endereços IP e sub-redes específicos é adicionar uma ACL para o Fastly no Commerce Admin. Veja a seguir as etapas com links para instruções mais detalhadas:

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira** > **Configuração do Fastly**.
1. [Criar uma nova ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) com uma lista de endereços IP ou sub-redes que você vai bloquear.
1. Adicione-o à lista de ACL e bloqueie conforme descrito em [Bloqueio](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) guia do módulo Fastly\_Cdn para o Adobe Commerce.

## Bloquear tráfego por país

Para o Adobe Commerce no armazenamento de infraestrutura em nuvem, a maneira mais eficiente de bloquear o tráfego por país(es) é adicionar uma ACL para o Fastly no Administrador do Commerce.

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira** > **Configuração do Fastly**.
1. Selecione os países e configure o bloqueio usando a ACL, conforme descrito na [Bloqueio](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) guia do módulo Fastly\_Cdn para o Adobe Commerce.

## Bloquear tráfego pelo agente do usuário

Para estabelecer o bloqueio com base no agente do usuário, é necessário adicionar um trecho de VCL personalizado à configuração do Fastly. Para fazer isso, siga estas etapas:

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira**.
1. Depois **Configuração do Fastly** > **Trechos de VCL Personalizados**.
1. Crie o novo trecho personalizado conforme descrito na seção [Trechos de VCL personalizados](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) guia para o módulo Fastly\_Cdn. Você pode usar a amostra de código a seguir como exemplo. Este exemplo não permite o tráfego para o `AhrefsBot` e `SemrushBot` agentes do usuário.

```php
name: block_bad_useragents
  type: recv
  priority: 5
  VCL:
  if ( req.http.User-Agent ~ "(AhrefsBot|SemrushBot)" ) {
      error 405 "Not allowed";
  }
```

## Limite de taxa (funcionalidade experimental Fastly)

Há uma funcionalidade experimental do Fastly para o Adobe Commerce na infraestrutura da nuvem, que permite especificar o limite de taxa para caminhos e rastreadores específicos. Consulte o [Documentação do módulo Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) para obter detalhes.

A funcionalidade deve ser amplamente testada no preparo, antes de ser usada na produção, pois pode bloquear o tráfego legítimo.

## Recomendado: considerar a atualização do robots.txt

Atualizar o `robots.txt` arquivo poderia ajudar a impedir que determinados mecanismos de pesquisa, rastreadores e robôs rastreassem determinadas páginas. Exemplos de páginas que não devem ser rastreadas são páginas de resultados de pesquisa, check-out, informações do cliente e assim por diante. Impedir que os robôs rastreem essas páginas pode ajudar a diminuir o número de solicitações geradas por esses robôs.

Há duas considerações importantes ao usar `robots.txt`:

* Os robôs podem ignorar o seu `robots.txt`. Especialmente os robôs malware, que verificam a Web em busca de vulnerabilidades de segurança, e os coletores de endereços de email usados por remetentes de spam não prestam atenção.
* A variável `robots.txt` é um arquivo disponível publicamente. Qualquer pessoa pode ver quais seções do servidor você não deseja que os robôs usem.

As informações básicas e o Adobe Commerce padrão `robots.txt` a configuração pode ser encontrada no [Robôs do mecanismo de pesquisa](https://docs.magento.com/m2/ee/user_guide/marketing/search-engine-robots.html) artigo em nossa documentação para desenvolvedores.

Para obter informações gerais e recomendações sobre `robots.txt`, consulte:

* [Criar um robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) arquivo pelo Suporte da Google
* [Sobre o /robots.txt](https://www.robotstxt.org/robotstxt.html) by robotstxt.org

Trabalhe com seu desenvolvedor e/ou especialista em SEO para determinar quais Agentes do usuário você deseja permitir ou aqueles que deseja proibir.

## Leitura relacionada

[Termos de licenciamento específicos do produto para o Adobe Commerce na nuvem](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
