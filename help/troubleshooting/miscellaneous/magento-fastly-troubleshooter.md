---
title: Solução de problemas do Adobe Commerce Fastly
description: Este solucionador de problemas do Fastly para usuários do Adobe Commerce guiará você até as soluções, com base na sua resposta sobre os sintomas exibidos. Clique nas perguntas para ver as próximas opções ou respostas.
exl-id: c5c51b89-5a7d-49ba-a0ee-7abbaf78fdad
feature: Support, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Solução de problemas do Adobe Commerce Fastly

Este solucionador de problemas do Fastly para usuários do Adobe Commerce guiará você até as soluções, com base na sua resposta sobre os sintomas exibidos. Clique nas perguntas para ver as próximas opções ou respostas.

## Etapa 1 - Verificar o serviço Fastly {#step-1}

+++**O cliente relata um problema envolvendo o Fastly. O serviço Fastly está inativo?**

a. SIM - Verificar [Status do serviço Fastly](https://status.fastly.com/), e [enviar um tíquete de suporte do Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).\
b. NÃO - Vá para [Etapa 2](#step-2).

+++

## Etapa 2 - Verificar arquivo de configuração de VCL {#step-2}

+++**Você tem erros ao executar o Testador de backend?**

Execute o URL do projeto por meio da [Testador de backend - Fastly](https://magento-tester.global.ssl.fastly.net/magento-tester/). Ela mostra a versão do arquivo de configuração de VCL, se a página for armazenável em cache, a versão do módulo Fastly e outras informações úteis para solução de problemas. Você tem algum erro?

a. SIM - Você tem a mensagem _A versão do VCL do plug-in está desatualizada! Faça upload novamente._ Para a solução desse erro, consulte [Erro do Fastly: a versão do VCL do plug-in está desatualizada! Faça upload novamente](/help/troubleshooting/miscellaneous/fastly-error-plugin-vcl-version-is-outdated-please-re-upload.md).\
b. NÃO - [Etapa 3](#step-3).

+++

## Etapa 3 - Verificar erro de otimização de imagem {#step-3}

+++**Erro de otimização de imagem?**

a. SIM - [Erro ao ativar a otimização de imagem](/help/troubleshooting/miscellaneous/error-enabling-image-optimization-in-magento-commerce.md).\
b. NÃO - verifique o DNS executando na CLI/terminal: `dig [your website.com] + short`. Vá para [Etapa 4](#step-4).

+++

## Etapa 4 - Verificar DNS {#step-4}

+++**O que acontece quando você corre `dig`?**

Quando você correu `dig` ele retornou um registro apontando para prod.magentocloud.map.fastly.net ou um dos seguintes endereços IP (consulte [Atualizar configuração DNS com configuração de produção](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns) na documentação do desenvolvedor):

* 151.101.1.124
* 151.101.65.124
* 151.101.129.124
* 151.101.193.124

a. SIM - O problema não está relacionado ao DNS. Vá para [Etapa 5](#step-5).\
b. NÃO - O problema provavelmente está relacionado ao DNS. O cliente deve [verificar configuração de DNS](https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns "https://devdocs.magento.com/cloud/live/site-launch-checklist.html#dns") ou entre em contato com o provedor de DNS para obter mais informações.

+++

## Etapa 5 - Confirmar conexão {#step-5}

+++**Você recebe uma mensagem de &quot;Conexão não segura&quot; ou &quot;Não segura&quot; ao executar `curl -svo /dev/null "https://website.com"` na CLI/terminal?**

a. SIM - isso provavelmente é um problema de certificado. Visite o site em um navegador, selecione o ícone de bloqueio e procure uma expiração de certificado. Vá para [Etapa 6](#step-6).\
b. NÃO - Visita [http://fastly-debug.com](https://www.fastly-debug.com/) e compartilhe essas informações em um [tíquete de suporte do Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

+++

## Etapa 6 - Confirmar se você tem um certificado TSL válido {#step-6}

+++**O certificado expirou?**

a. SIM - Você precisa renovar seu certificado TLS com a Autoridade de certificação (CA).\
b. NÃO - Você pode não ter um certificado. Se você tiver o Adobe Commerce, recomendamos que adquira um certificado TLS. Se você estiver na Adobe Commerce na infraestrutura em nuvem, poderá ter um certificado SSL/TLS validado por domínio para fornecer tráfego HTTPS seguro do Fastly. Consulte [provisionar certificados SSL/TLS](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) na documentação do desenvolvedor.

+++

[Voltar à Etapa 1](#step-1)
