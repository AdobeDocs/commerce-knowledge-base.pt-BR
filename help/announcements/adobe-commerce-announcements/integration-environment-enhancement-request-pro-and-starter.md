---
title: Solicitação de aprimoramento do ambiente de integração - Pro e Starter
description: Se você for um cliente de arquitetura de plano Adobe Commerce na infraestrutura em nuvem Pro e usar atualmente os Ambientes de integração de tamanho padrão, ou se for um cliente de arquitetura de plano Adobe Commerce na infraestrutura em nuvem Starter e usar atualmente o Ambiente de preparo de tamanho padrão e quiser mais potência, poderá solicitar uma atualização para Ambientes de integração aprimorados, que fornecem aproximadamente quatro vezes o desempenho. Este artigo separa as instruções para clientes Pro dos clientes Starter.
exl-id: c49b049b-efb8-412f-b27d-a89f8a758d85
feature: Integration
role: Admin
source-git-commit: fb26b71316e04de31fa6a895b87230bed5c1ca6a
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---

# Solicitação de aprimoramento do ambiente de integração - Pro e Starter

Se você for um cliente de arquitetura de plano Adobe Commerce na infraestrutura em nuvem Pro e usar atualmente os Ambientes de integração de tamanho padrão, ou se for um cliente de arquitetura de plano Adobe Commerce na infraestrutura em nuvem Starter e usar atualmente o Ambiente de preparo de tamanho padrão e quiser mais potência, poderá solicitar uma atualização para Ambientes de integração aprimorados, que fornecem aproximadamente quatro vezes o desempenho. Este artigo separa as instruções para clientes Pro dos clientes Starter.

>[!NOTE]
>
> Atualizar para a Integração aprimorada pode não resolver todos os problemas de desempenho, pois dependeria dos requisitos totais de recursos da sua instalação, incluindo integrações ou personalizações de terceiros.
>
> Você também precisa verificar se está seguindo as práticas recomendadas para obter o melhor desempenho no ambiente de integração e mesmo essa pode não ser uma solução completa. Consulte a documentação a seguir para obter orientação: [Arquitetura Pro](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture#integration-environment) e [Arquitetura inicial](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/starter-architecture#staging-environment) no Guia de infraestrutura do Commerce na nuvem.

## Pro

1. Se você for da categoria Pro, para atualizar, é necessário reduzir o número de ramificações de integração para dois (**a ramificação de integração principal está incluída no total**). **Observação: não conte a ramificação principal neste total. A ramificação primária não é considerada uma ramificação de integração.** Siga as etapas em [Gerenciar ramificações com o Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) na documentação do desenvolvedor.
1. O comerciante precisa [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando uma atualização para Ambientes de integração aprimorados, usando o motivo de contato &quot;*Solicitar uma alteração na configuração da nuvem*&quot;.
1. A equipe de engenharia de clientes do Adobe confirma o número de ambientes de integração e inicia a alteração.
1. O comerciante será notificado no tíquete quando a atualização for concluída.
1. O comerciante reimplanta os Ambientes de integração. Siga as etapas em [Mesclar uma ramificação](https://devdocs.magento.com/cloud/env/environments-start.html#merge) na documentação do desenvolvedor. *Nota*: a implantação ocorre automaticamente quando você executa: <pre>origem de push do git <branch-name></pre>

O aumento do desempenho indica uma atualização bem-sucedida para os Ambientes de integração aprimorados.

**Notas**:

* O tamanho padrão e o tamanho aprimorado são os dois únicos tamanhos disponíveis.
* Todos os Ambientes de integração de um determinado armazenamento têm o mesmo tamanho; eles não podem ser dimensionados independentemente.
* Se precisar de mais de dois dos Ambientes de integração aprimorada, consulte a equipe de conta do Adobe.

## Início

1. Os planos iniciais não podem ter ramificações de Integração: os comerciantes devem excluir os ambientes de Integração e deixar somente o ambiente de Preparo. Siga as etapas em [Gerenciar ramificações com o Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/console-branches.html) na documentação do desenvolvedor. O número de ambientes disponíveis será reduzido para permitir no máximo um Ambiente de integração.
1. O comerciante precisa [enviar um tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) solicitando uma Atualização para Ambientes de integração aprimorados, usando o motivo de contato *&quot;Solicitar uma alteração na configuração da nuvem&quot;* -  **seu ambiente de preparo é um ambiente de integração nomeado**.
1. A equipe de engenharia de clientes do Adobe confirma o número de ambientes de integração e inicia a alteração.
1. O comerciante será notificado no tíquete quando a atualização for concluída.
1. O comerciante reimplanta os Ambientes de integração. Siga as etapas em [Mesclar uma ramificação](https://devdocs.magento.com/cloud/env/environments-start.html#merge) na documentação do desenvolvedor. *Nota*: a implantação ocorre automaticamente quando você executa: <pre>origem de push do git <branch-name></pre>

O aumento do desempenho indica uma atualização bem-sucedida para os Ambientes de integração aprimorados.

**Notas**:

* O tamanho padrão e o tamanho aprimorado são os dois únicos tamanhos disponíveis.
* Todos os Ambientes de integração de um determinado armazenamento têm o mesmo tamanho; eles não podem ser dimensionados independentemente.
* Se precisar de Ambientes de integração além de Preparo, consulte a equipe de conta do Adobe.
* Caso a compra seja feita após 17 de setembro de 2020, esse aprimoramento não será aplicável devido aos Ambientes de integração ampliados.
