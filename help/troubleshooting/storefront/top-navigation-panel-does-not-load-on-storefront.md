---
title: O painel de navegação superior não é carregado na loja
description: Este artigo fornece soluções de configuração para problemas de ESI (Varnish Edge Side Includes), em que o conteúdo de determinadas páginas, geralmente o painel de navegação superior, não é exibido na loja se o Verniz for usado para o armazenamento em cache.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# O painel de navegação superior não é carregado na loja

Este artigo fornece soluções de configuração para problemas de ESI (Varnish Edge Side Includes), em que o conteúdo de determinadas páginas, geralmente o painel de navegação superior, não é exibido na loja se o Verniz for usado para o armazenamento em cache.

## Produtos e versões afetados

* Adobe Commerce 2.X.X
* Todas as versões em verniz

## Problema

<u>Pré-requisitos</u>:

Instale e configure o Varnish para sua loja da Adobe Commerce.

<u>Etapas a serem reproduzidas</u>:

1. Vá para a loja.
1. Navegue pelas páginas da loja.

<u>Resultados esperados</u>:

Todo o conteúdo e todos os blocos de página foram carregados com sucesso.

<u>Resultados reais</u>:

Observe que alguns blocos de conteúdo, como o painel de navegação superior com categorias, não estão carregando. Em vez disso, é exibido um espaço em branco.

## Causa

As possíveis razões para o problema são as seguintes:

* As tags de inclusão ESI são geradas com protocolo de acesso HTTPS, enquanto o verniz funciona somente com HTTP.
* O verniz não processa ESI dentro do JSON.
* Os cabeçalhos de resposta são muito grandes para o verniz; não é possível processá-los.

## Solução

Para resolver os problemas, você precisa executar uma configuração adicional de Verniz e reiniciar o Verniz.

1. Como usuário com `root` abrir o arquivo de configuração Vanish em um editor de texto. Consulte a [Modificar a configuração do sistema Vernish](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) na documentação do desenvolvedor, para obter informações sobre onde esse arquivo pode estar localizado para diferentes sistemas operacionais.
1. No `DAEMON_OPTS variable`, adicionar `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check`. Isso seria semelhante a:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Salve as alterações e saia do editor de texto.
1. No arquivo de configuração do VCL, aumente os cabeçalhos de resposta aumentando os valores desses parâmetros: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Verifique se os dois últimos têm valores semelhantes.
1. Quando você altera isso, é necessário executar o `service varnish restart` para que as alterações entrem em vigor.

## Leitura relacionada

* [Configurar o Varnish e o servidor Web](https://devdocs.magento.com/guides/v2.3/config-guide/varnish/config-varnish-configure.html#config-varnish-config-sysvcl) na documentação do desenvolvedor.
* [Documentação de verniz](https://varnish-cache.org/docs/5.1/reference/index.html)
