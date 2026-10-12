---
title: Testar o Fastly na produção se um Site Ativo usar o mesmo domínio
description: Se você tiver um site ativo em execução no domínio de produção ("example.com") e precisar testar sua nova loja no ambiente de produção do Adobe Commerce na infraestrutura em nuvem com o Fastly CDN habilitado, recomendamos usar o subdomínio (como "prod.example.com"), tendo adicionado anteriormente ao Fastly, para qualquer atividade de teste de pré-lançamento. Este artigo discute os detalhes e fornece links úteis para os recursos de documentação do Adobe Commerce relacionados.
exl-id: bc9d11c8-ce47-461d-b5b8-c03494bc4ceb
feature: Cache
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%
---
# Testar o Fastly na produção se um Site Ativo usar o mesmo domínio

Se você tiver um site ativo em execução em seu domínio de produção (`example.com`) e precisar testar seu novo armazenamento no ambiente de Produção do Adobe Commerce na infraestrutura em nuvem com o CDN do Fastly habilitado, recomendamos usar o subdomínio (como `prod.example.com`), que já o adicionou ao Fastly, para qualquer atividade de teste de pré-lançamento. Este artigo discute os detalhes e fornece links úteis para os recursos de documentação do Adobe Commerce relacionados.

## Problema

O armazenamento atual que usa o domínio de produção `example.com` está ativo e em funcionamento. No entanto, é necessário testar sua nova loja, criada com o Adobe Commerce na infraestrutura em nuvem e implantada no ambiente de produção, com o serviço de cache de página completa do Fastly habilitado.

O problema é que o ambiente de Produção do seu projeto Adobe Commerce na infraestrutura em nuvem usa o mesmo domínio ativo (`example.com`), e você não pode alternar seu novo site para esse domínio, executando simultaneamente seu armazenamento ativo atual - no mesmo domínio.

### Por que usar o Fastly para testar o ambiente de Produção?

Em teoria, você poderia ignorar o uso do Fastly CDN e testar seu Adobe Commerce no armazenamento de infraestrutura na nuvem no ambiente de Produção sem o cache de página completa habilitado.

No entanto, com o cache de página inteira ativado, sua loja tem um desempenho diferente; você nunca saberá o desempenho real em tempo real do site se não o tiver testado com CDN antes de iniciar. Testar seu armazenamento na produção com o Fastly CDN habilitado é a recomendação oficial do Adobe Commerce.

## Solução: use o subdomínio de produção

Use o subdomínio de primeiro nível (`prod.example.com`) para seu novo armazenamento do Adobe Commerce na infraestrutura de nuvem no ambiente de Produção enquanto mantém o site ativo atual no domínio base (`example.com`).

Ao planejar seu projeto do Adobe Commerce na infraestrutura em nuvem, você pode especificar esse subdomínio de produção e solicitar que a equipe de infraestrutura em nuvem aponte o subdomínio para o serviço Fastly.

Siga estas etapas para processar o subdomínio no projeto de infraestrutura do Adobe Commerce na nuvem:

* [Envie um tíquete de suporte](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) solicitando a adição do subdomínio à configuração Fastly service/Nginx (para a arquitetura de plano do Adobe Commerce na infraestrutura em nuvem Pro).
* Defina as configurações de DNS correspondentes no seu lado.

Depois de executar as etapas para configuração de subdomínio, você também deve seguir estas etapas para validar o domínio de produção para o certificado SSL:

* Faça upload do registro TXT de DNS para validação SSL do seu domínio de produção.
* [Envie um tíquete de suporte](https://experienceleague.adobe.com/pt-br/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) solicitando a validação do domínio de produção para o certificado SSL.

O uso do subdomínio permite executar uma &quot;inicialização suave&quot; do armazenamento no futuro, pois essa inicialização requer apenas a atualização das configurações de DNS correspondentes.

## Documentação relacionada

Em nossa base de conhecimento de suporte:

* [Definição das configurações de DNS do Fastly nos ambientes de Preparo e Produção](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/configure-fastly-dns-settings-on-staging-and-production-environments.html?lang=pt-BR)
* [Possíveis bloqueadores para lançamento no Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/blockers-launching-on-magento-commerce-cloud.html?lang=pt-BR)

Em nossa documentação do desenvolvedor:

* [Visão geral do Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=pt-BR)
* [Lista de verificação de ativação: configurações de DNS do Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/launch/checklist.html?lang=pt-BR)
