---
title: Erro ao limpar o cache do Fastly na Nuvem (A solicitação de limpeza não foi processada com êxito)
description: '"Este artigo fornece uma correção para quando você usa uma opção de limpeza do Fastly e recebe o erro: *A solicitação de limpeza não foi processada com êxito*. O Fastly é um serviço de CDN e armazenamento em cache incluído no Adobe Commerce para planos e implementações de infraestrutura em nuvem. Se você tentar usar uma opção de limpeza do Fastly sem processar, talvez você tenha credenciais incorretas no ambiente ou tenha encontrado um problema.'''
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Erro ao limpar o cache do Fastly na Nuvem (A solicitação de limpeza não foi processada com êxito)

Este artigo fornece uma correção para quando você usa uma opção de limpeza Fastly e recebe o erro: *A solicitação de limpeza não foi processada com êxito*. O Fastly é um serviço de CDN e armazenamento em cache incluído no Adobe Commerce para planos e implementações de infraestrutura em nuvem. Se você tentar usar uma opção de limpeza do Fastly sem processar, talvez você tenha credenciais incorretas no ambiente ou tenha encontrado um problema.

Estas informações ajudam a verificar e testar os cabeçalhos do Fastly no site ativo e nos servidores de origem.

## Versões afetadas

* Adobe Commerce na infraestrutura em nuvem 2.1.X e posterior
* Fastly 1.2.27 e posterior

## Problema

O armazenamento em cache está funcionando, mas quando você tenta limpar, você recebe um erro ou ele não funciona. O erro inclui: &quot;A solicitação de limpeza não foi processada com êxito.&quot;

## Causa

Talvez você tenha credenciais incorretas definidas no ambiente ou precise fazer upload de trechos de VCL.

## Resolver

### Verificar credenciais do Fastly

Verifique se você tem a ID de serviço Fastly e o token da API no seu ambiente. Se você tiver credenciais de armazenamento temporário em produção, as remoções podem não ser processadas ou processadas incorretamente.

1. Faça logon no Administrador local do Commerce como administrador.
1. Clique em **Lojas** > Configurações > **Configuração** > **Avançado** > **Sistema** e expanda **Cache de Página Inteira**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Expanda Configuração do Fastly e verifique a ID do Serviço Fastly e o token da API para seu ambiente.
1. Se você modificar os valores, clique em Testar credenciais.

### Verificar trechos de VCL

Se as credenciais estiverem corretas, você poderá ter problemas com suas VCLs. Para listar e revisar suas VCLs por serviço, insira a seguinte chamada de API em um terminal:

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Revise a lista de VCLs. Se tiver problemas com os VCLs padrão do Fastly, você poderá carregar novamente ou verificar o conteúdo de acordo com os [VCLs padrão do Fastly](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Para editar seus VCLs personalizados, consulte [Fragmentos de VCL personalizados](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) no Guia de Infraestrutura do Commerce na Nuvem.

## Mais informações

Em nossa documentação do desenvolvedor:

* [Sobre o Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Configurar Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Snippets de VCL Fastly personalizados](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
