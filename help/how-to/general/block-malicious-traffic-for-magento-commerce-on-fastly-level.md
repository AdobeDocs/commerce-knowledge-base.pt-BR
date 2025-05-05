---
title: Bloquear tráfego mal-intencionado para o Adobe Commerce no nível Fastly
description: Este artigo fornece as etapas que você pode seguir para bloquear tráfego mal-intencionado quando suspeitar que o Adobe Commerce na loja de infraestrutura na nuvem está enfrentando um ataque de DDoS.
exl-id: 1a834a0a-753b-432e-9c3b-ef8dd034d294
feature: Cache, Marketing Tools
source-git-commit: b58e182c64b3fad508145d9078619ddbe0e2b887
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Bloquear tráfego mal-intencionado para o Adobe Commerce no nível Fastly

Este artigo fornece as etapas que você pode seguir para bloquear tráfego mal-intencionado quando suspeitar que o Adobe Commerce na loja de infraestrutura na nuvem está enfrentando um ataque de DDoS.

## Produtos e versões afetados:

* Adobe Commerce na infraestrutura em nuvem 2.3.x

Neste artigo, pressupomos que você já tenha os IPs mal-intencionados e/ou seu país e agentes do usuário. Normalmente, os usuários do Adobe Commerce na infraestrutura em nuvem obteriam essas informações do suporte da Adobe Commerce. As seções a seguir fornecem etapas para bloquear o tráfego com base nessas informações. Todas as alterações devem ser feitas no ambiente de Produção.

## Obter acesso ao Painel de administração

Se o seu site for sobrecarregado pelo DDoS, talvez você não consiga fazer logon no Commerce Admin (e executar todas as etapas descritas mais adiante neste artigo).

Para obter acesso ao Administrador, coloque o site no modo de manutenção, conforme descrito em [Habilitar ou desabilitar o modo de manutenção](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) e inclua o endereço IP na lista de permissões. Desative o modo de manutenção depois que isso for concluído.

## Bloquear tráfego por IP

Para o Adobe Commerce no armazenamento de infraestrutura em nuvem, a maneira mais eficiente de bloquear o tráfego por endereços IP e sub-redes específicos é adicionar uma ACL para o Fastly no Commerce Admin. Veja a seguir as etapas com links para instruções mais detalhadas:

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira** > **Configuração do Fastly**.
1. [Crie uma nova ACL](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/ACL.md) com uma lista de endereços IP ou sub-redes que você vai bloquear.
1. Adicione-o à lista de ACL e bloqueie conforme descrito no guia [Bloqueio](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) do módulo Fastly\_Cdn para o Adobe Commerce.

## Bloquear tráfego por país

Para o Adobe Commerce no armazenamento de infraestrutura em nuvem, a maneira mais eficiente de bloquear o tráfego por país(es) é adicionar uma ACL para o Fastly no Administrador do Commerce.

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira** > **Configuração do Fastly**.
1. Selecione os países e configure o bloqueio usando ACL conforme descrito no guia [Bloqueio](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/BLOCKING.md) do módulo Fastly\_Cdn para o Adobe Commerce.

## Bloquear tráfego pelo agente do usuário

Para estabelecer o bloqueio com base no agente do usuário, é necessário adicionar um trecho de VCL personalizado à configuração do Fastly. Para fazer isso, siga estas etapas:

1. No Administrador do Commerce, navegue até **Lojas** > **Configuração** > **Avançado** > **Sistema** > **Cache de Página Inteira**.
1. Então **Configuração Fastly** > **Snippets de VCL Personalizado**.
1. Crie o novo trecho personalizado conforme descrito no guia [Trechos de VCL personalizados](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/CUSTOM-VCL-SNIPPETS.md) para o módulo Fastly\_Cdn. Você pode usar a amostra de código a seguir como exemplo. Este exemplo não permite o tráfego para os agentes de usuário `AhrefsBot` e `SemrushBot`.

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

Há uma funcionalidade experimental do Fastly para o Adobe Commerce na infraestrutura da nuvem, que permite especificar o limite de taxa para caminhos e rastreadores específicos. Consulte a [documentação do módulo Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/RATE-LIMITING.md) para obter detalhes.

A funcionalidade deve ser amplamente testada no preparo, antes de ser usada na produção, pois pode bloquear o tráfego legítimo.

## Recomendado: considerar a atualização do robots.txt

A atualização do arquivo `robots.txt` pode ajudar a impedir que determinados mecanismos de pesquisa, rastreadores e robôs rastreiem determinadas páginas. Exemplos de páginas que não devem ser rastreadas são páginas de resultados de pesquisa, check-out, informações do cliente e assim por diante. Impedir que os robôs rastreem essas páginas pode ajudar a diminuir o número de solicitações geradas por esses robôs.

Há duas considerações importantes ao usar o `robots.txt`:

* Robôs podem ignorar seu `robots.txt`. Especialmente os robôs malware, que verificam a Web em busca de vulnerabilidades de segurança, e os coletores de endereços de email usados por remetentes de spam não prestam atenção.
* O arquivo `robots.txt` é um arquivo disponível publicamente. Qualquer pessoa pode ver quais seções do servidor você não deseja que os robôs usem.

As informações básicas e a configuração padrão do Adobe Commerce `robots.txt` podem ser encontradas no artigo [Robôs do Mecanismo de Pesquisa](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/marketing/seo/seo-overview#search-engine-robots) da documentação do desenvolvedor.

Para obter informações gerais e recomendações sobre `robots.txt`, consulte:

* [Criar um arquivo robots.txt](https://developers.google.com/search/docs/advanced/robots/create-robots-txt) pelo Suporte da Google
* [Sobre /robots.txt](https://www.robotstxt.org/robotstxt.html) de robotstxt.org

Trabalhe com seu desenvolvedor e/ou especialista em SEO para determinar quais Agentes do usuário você deseja permitir ou aqueles que deseja proibir.

## Leitura relacionada

* [Termos de Licenciamento Específicos do Produto para o Adobe Commerce na Nuvem](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeCommerceCloud-WW-2023v1.pdf)
* [VCL personalizado para solicitações de bloqueio](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking) no Guia do Commerce na Nuvem
