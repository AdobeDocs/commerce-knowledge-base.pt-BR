---
title: Mensagem de erro ao adicionar sites à Verificação de segurança
description: Este artigo fornece soluções possíveis para o problema quando um usuário não consegue adicionar sites à [Verificação de segurança da Commerce](https://account.magento.com/scanner/dashboard/).
exl-id: 8d000ca4-b977-432d-bb26-6ea320067a40
feature: Cache, Compliance, Console, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%
---
# Mensagem de erro ao adicionar sites à Verificação de segurança

Este artigo fornece soluções possíveis para o problema quando um usuário não consegue adicionar sites à [Verificação de Segurança do Commerce](https://account.magento.com/scanner/dashboard/).

## Produtos e versões afetados

* Adobe Commerce (todos os métodos e versões de implantação)
* Magento Open Source

## Problema

O usuário não pode adicionar sites à [Verificação de Segurança do Commerce](https://account.magento.com/scanner/dashboard/). A seguinte mensagem de erro é exibida ao tentar adicionar um site: *Não é possível enviar o site para verificação.*

## Solução

1. Verifique se os seguintes endereços IP não estão bloqueados nas portas 80 e 443:
   * 52.87.98.44
   * 34.196.167.176
   * 3.218.25.102

1. O código de confirmação diferencia tempo. Se mais de 30 minutos tiverem se passado depois que o link **Adicionar site** tiver sido clicado, o código provavelmente terá expirado.
1. Não se esqueça de limpar o cache e garantir que o código de validação apareça no corpo de origem da página inicial. O código de confirmação deve ser inserido de acordo com as especificações de marcação do HTML: o comentário do HTML pode ser inserido no corpo da página (sugerimos colocá-lo na seção de rodapé); a tag do META deve estar somente na seção de cabeçalho.
1. Antes de clicar em **Verificar código de confirmação**, abra o console de desenvolvedor do navegador, clique na guia **Rede** e verifique a resposta de magento.com. Ele deve ser HTTP 200 (OK) e o corpo da resposta deve conter um objeto JSON.
1. Se o código de resposta for HTTP 200, o corpo da resposta for um objeto JSON e o valor da propriedade `verified` for `false`, significa que o código não foi encontrado na página. O valor da propriedade `details` deve conter a explicação. Por exemplo, se o armazenamento usar um certificado SSL autoassinado, provavelmente haverá um erro de conexão.

Se ainda não conseguir adicionar sites, conclua as seguintes etapas:

1. Coloque outro comentário do HTML na página:

   ```HTML
   <!-- MAGEID:Your magento.com ID, EMAIL:your email address -->
   ```

1. Envie um tíquete de suporte e forneça as seguintes informações:
   * URL de loja da Adobe Commerce
   * MAGEID + email da conta Magento.com
   * Nome + Sobrenome
   * Nome da empresa
   * Lista de emails de notificação separados por vírgulas

## Leitura relacionada

* [Verificação de segurança](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) em nosso guia do usuário.
