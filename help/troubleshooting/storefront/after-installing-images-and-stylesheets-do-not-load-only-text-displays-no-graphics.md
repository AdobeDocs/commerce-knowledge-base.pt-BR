---
title: Após a instalação, as imagens e folhas de estilos não são carregadas; somente o texto é exibido, sem gráficos
description: Este artigo descreve os possíveis motivos e soluções para o problema em que as folhas de estilos e imagens não são carregadas após a instalação do Adobe Commerce.
exl-id: f33cee89-b416-4d63-8cc5-9cc57618ce92
feature: Install, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# Após a instalação, as imagens e folhas de estilos não são carregadas; somente o texto é exibido, sem gráficos

Este artigo descreve os possíveis motivos e soluções para o problema em que as folhas de estilos e imagens não são carregadas após a instalação do Adobe Commerce.

## Produtos e versões afetados

* Adobe Commerce 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

<u>Etapas a serem reproduzidas</u>

1. Instale o Adobe Commerce.
1. Navegue até a vitrine ou o Administrador.

<u>Resultado esperado</u>

Os estilos são aplicados, nenhum elemento da interface do usuário parece ter estilos ausentes.

<u>Resultado real</u>

Os estilos não são aplicados corretamente, gráficos estão ausentes.

## Causa

O caminho para imagens e folhas de estilos não está correto, devido a um URL base incorreto ou porque as regravações do servidor (CentOS, Ubuntu) não estão configuradas corretamente.

Para confirmar esse é o caso, use um inspetor de navegador da Web para verificar os caminhos para ativos estáticos e se esses ativos estão localizados no sistema de arquivos Adobe Commerce ou Magento Open Source.

Os ativos estáticos estão localizados em `<magento_root>/pub/static/` , no prazo de `frontend` e `adminhtml` diretórios.

## Solução

As soluções possíveis a seguir dependem do software usado e da causa do problema:

* Se estiver usando o servidor Web Apache, verifique se [regravações de servidor](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/apache.html#apache-help-rewrite) e o URL base do servidor Adobe Commerce/Magento Open Source e tente novamente. Se você configurar o Apache `AllowOverride` diretiva incorretamente, os arquivos estáticos não são fornecidos no local correto.
* Se você estiver usando o servidor Web nginx, certifique-se de [configurar um arquivo de host virtual](https://devdocs.magento.com/guides/v2.3/install-gde/prereq/nginx.html#configure-nginx-ubuntu). O arquivo de host virtual nginx deve atender aos seguintes critérios:
   * A variável `include` A diretiva deve apontar para o exemplo de arquivo de configuração nginx no diretório de instalação do Adobe Commerce/Magento Open Source. Por exemplo:    `include /var/www/html/magento2/nginx.conf.sample;`
   * A variável `server_name` diretiva deve corresponder ao URL base que você especificou ao instalar o Adobe Commerce/Magento Open Source. Por exemplo: `server_name 192.186.33.10;`
* Se o aplicativo estiver em [modo de produção](https://devdocs.magento.com/guides/v2.3/config-guide/bootstrap/magento-modes.html#production-mode), tente implantar arquivos de exibição estáticos usando o `magento setup:static-content:deploy` comando. Para obter detalhes sobre a implantação de arquivos estáticos, consulte [Implantar arquivos de exibição estáticos](https://devdocs.magento.com/guides/v2.3/install-gde/install/cli/install-cli-subcommands-maint.html) na documentação do desenvolvedor.
