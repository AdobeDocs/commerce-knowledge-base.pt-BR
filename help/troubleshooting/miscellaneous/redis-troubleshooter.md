---
title: Solução de problemas do Redis no Adobe Commerce
description: Este artigo é uma ferramenta de solução de problemas para usuários locais do Adobe Commerce e do Adobe Commerce em infraestrutura em nuvem que têm problemas com o Redis. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas. Dependendo dos sintomas e da configuração, o solucionador de problemas explicará como solucionar problemas de versão e memória e otimizar o desempenho.
exl-id: 241abcfd-33b8-449b-b385-32950bd26320
feature: Services, Support
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Solução de problemas do Redis no Adobe Commerce

Este artigo é uma ferramenta de solução de problemas para usuários locais do Adobe Commerce e do Adobe Commerce em infraestrutura em nuvem que têm problemas com o Redis. Clique em cada pergunta para revelar a resposta em cada etapa da solução de problemas. Dependendo dos sintomas, a solução de problemas explicará como você pode solucionar problemas de versão e memória e otimizar o desempenho.

## Etapa 1 - Redefinir problema {#step-1}

+++Problema de Redis?

a. SIM - Vá para [Etapa 2](#step2)</a>.

b. NÃO - Retornar para [support.magento.com](https://support.magento.com/hc/en-us) e procure por artigos relevantes para a solução de problemas.

+++

## Etapa 2 - Confirmar os patches do Redis instalados {#step-2}

+++Patches Redis atuais instalados?

a. SIM - Vá para [Etapa 3](#step3)</a>.

b. NÃO - Verifique se você tem a versão mais recente do pacote `magento-cloud-patches` instalado. Este pacote tem os patches necessários para o Redis. Para acessar, acesse [Magneto-cloud-patches do GitHub](https://github.com/magento/magento-cloud-patches/).

+++

## Etapa 3 - Confirmar se a versão do Redis é compatível {#step-3}

+++No Redis versões 3.2 ou 5.0?

Verifique executando os seguintes comandos na CLI. Pro ou armazenamento temporário: `$ redis-cli -p %port-number% info | grep redis_version`, onde `%port-number%` é o número da porta, que pode ser encontrado no campo `app/etc/env.php` ou executando um destes comandos: `$ vendor/bin/ece-tools env:config:show | grep -i redis -A 3` ou `$ cat app/etc/env.php | grep redis -A 3` Início ou integração: `$ redis-cli -h 'redis.internal' info | grep redis_version`

a. SIM - Vá para [Etapa 4](#step4).

b. NÃO - a Adobe Commerce oferece suporte às versões 3.2 e 5.0 do Redis. Se você estiver executando o Adobe Commerce na infraestrutura em nuvem 2.3.3 ou superior, recomendamos atualizar para o Redis 5. Para obter etapas de configuração sobre a arquitetura do plano Pro da infraestrutura em nuvem do Adobe Commerce, ambientes de Integração e Início, incluindo a ramificação mestre, consulte [Adobe Commerce na infraestrutura em nuvem > Configurar o serviço Redis](https://devdocs.magento.com/cloud/project/services-redis.html)</a> na documentação do desenvolvedor. **É necessário [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) para alterar a configuração do serviço nos ambientes de produção e preparo da arquitetura Pro. Além disso, para o Adobe Commerce na infraestrutura em nuvem e o Adobe Commerce no local 2.3.5+, recomenda-se a implementação do cache Redis estendido. Esse tipo de implementação do cache Redis fornece melhorias que minimizam o número de consultas a Redis que são executadas em cada solicitação Adobe Commerce. Para obter etapas, consulte [Implementação do cache Redis estendido Adobe Commerce 2.3.5+](https://support.magento.com/hc/en-us/articles/360049292532) em nossa base de conhecimento de suporte. Para todos os outros usuários do Adobe Commerce, consulte [Guia de configuração do Adobe Commerce > Configurar Redis](https://devdocs.magento.com/guides/v2.4/config-guide/redis/config-redis.html) na documentação do desenvolvedor, para obter etapas.

+++

## Etapa 4 - Verificar a versão mais recente de ECE-Tools {#step-4}

+++Você tem a versão mais recente do [Ferramentas ECE > v2002.1.1](https://github.com/magento/ece-tools/releases)?

Verifique qual versão você tem executando o comando no CLI/Terminal: `$php vendor/bin/composer info magento/ece-tools`.

a. SIM - Vá para [Etapa 5](#step5).

b. NÃO - [Atualizar ECE-Tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html) para a versão mais recente.

+++

## Etapa 5 - Avaliar o tráfego de rede {#step-5}

+++Há muito tráfego de rede entre o aplicativo e o Redis?

a. SIM - Tente o seguinte: para uma arquitetura não dividida, verifique se uma [conexão secundária](/help/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.md) é usada. Para arquitetura dividida, a variável [O cache L2 deve estar habilitado](https://devdocs.magento.com/guides/v2.4/config-guide/cache/two-level-cache.html).

b. NÃO - Define a configuração do cache L2 utilizando [Atualizando backend Redis](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend). Vá para [Etapa 6](#step6).

+++

## Etapa 6 - Verificar a velocidade do site {#step-6}

+++O site ainda está funcionando lentamente após ativar o cache L2?

a. SIM - Verifique o diretório temporário `/dev/shm` para ver se é necessário aumentar o espaço. Se precisar de mais espaço, [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).
b. NÃO - A ativação do cache L2 parece ter resolvido seus problemas com o Redis.

+++

[Voltar à Etapa 1](#step-1)
