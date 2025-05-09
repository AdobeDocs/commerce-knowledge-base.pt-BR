---
title: Alocar mais espaço para o MySQL no Adobe Commerce na nuvem
description: Este artigo fornece instruções sobre como alocar mais espaço para o MySQL no Adobe Commerce na infraestrutura em nuvem.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Alocar mais espaço para o MySQL no Adobe Commerce na nuvem


## Alocar espaço na Integração do plano inicial e do plano Pro

Para todos os ambientes de plano Starter e plano Pro [ambiente de integração](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md), é possível alocar mais espaço para MySQL no arquivo `.magento/services.yaml`, aumentando o parâmetro `mysql: disk:`. Por exemplo:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Consulte o artigo [Configurar serviço MySQL](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/configure/service/mysql) para referência.

Depois de alterar o arquivo `.magento/services.yaml`, você precisa confirmar e enviar suas alterações para que elas sejam aplicadas. O push acionará o processo de implantação.

>[!WARNING]
>
>Uma partição de plano inicial nunca deve ser menor (por exemplo, passando de 30 GB para 20 GB), pois isso provavelmente resultará em corrupção de dados catastrófica.

## Alocar espaço em produção ou preparo de plano Pro

Para fazer essas alterações para o ambiente de preparo ou produção do plano Pro, você deve criar um [tíquete de suporte](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed). Ao enviar um tíquete de suporte para aumentar o armazenamento, o suporte precisará saber a quantidade e a qual partição o armazenamento deve ser aplicado (`/mysql` ou `/exports`). Uma solicitação de aumento de armazenamento requer a aprovação da equipe de conta do Adobe, que verificará a quantidade de armazenamento que você tem direito (de acordo com o formulário de pedido) antes da aprovação.

## Diminuição do espaço alocado não disponível (plano Pro e Starter)

O Suporte Adobe Commerce pode aumentar uma partição (`/mysql` ou `/exports`), mas não pode reduzir uma partição. Há risco de corrupção de dados ao fazer isso, por isso a diminuição do armazenamento para uma partição não está disponível.
Também é verdade para o plano Inicial, em que você mesmo pode aumentar o espaço alocado: diminuir não é altamente recomendado e pode resultar em corrupção de dados catastrófica.
