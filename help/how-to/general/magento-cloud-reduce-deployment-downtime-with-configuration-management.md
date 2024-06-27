---
title: Reduza o tempo de inatividade da implantação no Adobe Commerce na infraestrutura em nuvem
description: Para reduzir drasticamente o tempo de inatividade de manutenção e fornecer uma configuração eficiente da sua loja em todos os ambientes, a infraestrutura do Adobe Commerce na nuvem fornece o recurso **Gerenciamento de configuração**. Para implementações do Adobe Commerce na infraestrutura em nuvem 2.2.x e posteriores, esse recurso é compatível com conceitos e opções de Implantação de pipeline com etapas reduzidas.
exl-id: fde3571c-d95c-4a9b-a024-3b29f9c491ab
feature: Build, Cloud, Configuration, Deploy
source-git-commit: 23d957ceac17f9989d14b215582304199d398545
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Reduza o tempo de inatividade da implantação no Adobe Commerce na infraestrutura em nuvem

Para reduzir drasticamente o tempo de inatividade de manutenção e fornecer uma configuração eficiente da sua loja em todos os ambientes, a infraestrutura do Adobe Commerce na nuvem fornece a **Gerenciamento de configurações** recurso. Para implementações do Adobe Commerce na infraestrutura em nuvem 2.2.x e posteriores, esse recurso é compatível com conceitos e opções de Implantação de pipeline com etapas reduzidas.

## Visão geral

Os problemas dolorosos e demorados da implantação do armazenamento da Web incluem:

* **Aplicar a mesma configuração em todos os ambientes.** Normalmente, você insere configurações manualmente ou por meio de atualizações complicadas do banco de dados. Com o Gerenciamento de configurações, você exporta configurações do banco de dados em um único arquivo para depois enviá-lo com seu código do ambiente de desenvolvimento local para Integração, Preparo e Produção.

* **Tempo de inatividade do site ao implantar conteúdo estático.** Normalmente, o conteúdo estático é implantado durante o [fase de implantação](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase). Isso pode levar até 30 minutos ou mais, o que não é aceitável para a empresa. O Gerenciamento de configurações move a implantação de conteúdo estático para o [fase de criação](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase), que não requer tempo de inatividade.

## Versões da tecnologia

* Adobe Commerce na infraestrutura em nuvem **2.1.4** e posterior para o Gerenciamento de configuração
* Adobe Commerce na infraestrutura em nuvem **2.2** e posteriores para Gerenciamento de configuração/Implantação de pipeline

## O que é o gerenciamento de configuração

Para encurtar a história, o processo de Gerenciamento de configurações (também conhecido como Implantação de pipeline) extrai todas as configurações do seu Adobe Commerce na implementação da infraestrutura em nuvem (banco de dados) em um único arquivo PHP. Em seguida, você adiciona o arquivo ao Git commit e o envia por push em todos os seus ambientes.

Isso oferece os seguintes benefícios:

* **Configurações consistentes em todos os ambientes:** todas as configurações exportadas para o arquivo de configuração são bloqueadas (os campos correspondentes no Commerce Admin se tornam somente leitura), o que garante configurações consistentes à medida que você envia o arquivo por todos os ambientes.
* **Tempo de inatividade reduzido:** a implantação do arquivo estático muda de [fase de implantação](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#deploy-phase-deploy-phase) (que exige que o site esteja no modo de Manutenção) para o [fase de criação](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process#build-phase-build-phase) (quando o site não estiver no modo de Manutenção e não será desativado se ocorrerem erros ou problemas).
* **Dados confidenciais protegidos:** com o Adobe Commerce na infraestrutura em nuvem 2.2 e posterior, o processo também exporta dados confidenciais (por exemplo, credenciais de gateway de pagamento) para o `env.php` arquivo. Esse arquivo só deve ser salvo no ambiente em que foi criado e não enviado com suas ramificações Git.

É altamente recomendável aplicar a abordagem de Gerenciamento de configuração na sua implantação.

## Gerenciamento de configuração na documentação do desenvolvedor

* [Gerenciamento de configuração para **2.1.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) e a variável [exemplo](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) no *Guia da infraestrutura do Adobe Commerce na nuvem*
* [Gerenciamento de configuração para **2.2.X**](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) e a variável [exemplo](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html) no *Guia da infraestrutura do Adobe Commerce na nuvem*
* [Atualizar do 2.0.X ou 2.1.X](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html#upgrade-from-older-versions) seção do *Atualização do Adobe Commerce na infraestrutura em nuvem* tópico
* [Implantação de pipeline](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/overview.html) no *Guia de configuração do Adobe Commerce na infraestrutura em nuvem* - Para o Adobe Commerce na infraestrutura em nuvem, não é necessário seguir as instruções neste guia. O conteúdo é estritamente para referência. Já fornecemos o servidor de criação, ambientes de integração e muito mais com o Adobe Commerce na infraestrutura em nuvem.
