---
title: Alocar mais espaço para o MySQL no Adobe Commerce na nuvem
description: Este artigo fornece instruções sobre como alocar mais espaço para o MySQL no Adobe Commerce na infraestrutura em nuvem.
exl-id: 98501aa0-5ec7-4ea1-8856-13d171ad0be9
feature: Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%
---
# Alocar mais espaço para o MySQL no Adobe Commerce na nuvem


## Alocar espaço na Integração do plano inicial e do plano Pro

Para todos os ambientes de plano Starter e plano Pro [ambiente de integração](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242), é possível alocar mais espaço para MySQL no arquivo `.magento/services.yaml`, aumentando o parâmetro `mysql: disk:`. Por exemplo:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Consulte o artigo [Configurar serviço MySQL](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/mysql) para referência.

Depois de alterar o arquivo `.magento/services.yaml`, você precisa confirmar e enviar suas alterações para que elas sejam aplicadas. O push acionará o processo de implantação.

>[!WARNING]
>
>Uma partição de plano inicial nunca deve ser menor (por exemplo, passando de 30 GB para 20 GB), pois isso provavelmente resultará em corrupção de dados catastrófica.

## Alocar espaço em produção ou preparo de plano Pro

Para fazer essas alterações para o ambiente de preparo ou produção do plano Pro, você deve criar um [tíquete de suporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide). Ao enviar um tíquete de suporte para aumentar o armazenamento, o suporte precisará saber a quantidade e a qual partição o armazenamento deve ser aplicado (`/mysql` ou `/exports`). Uma solicitação de aumento de armazenamento requer a aprovação da equipe de conta da Adobe, que verificará a quantidade de armazenamento que você tem direito (de acordo com o formulário de pedido) antes da aprovação.

## Diminuição do espaço alocado não disponível (plano Pro e Starter)

O Suporte Adobe Commerce pode aumentar uma partição (`/mysql` ou `/exports`), mas não pode reduzir uma partição. Há risco de corrupção de dados ao fazer isso, por isso a diminuição do armazenamento para uma partição não está disponível.
Também é verdade para o plano Inicial, em que você mesmo pode aumentar o espaço alocado: diminuir não é altamente recomendado e pode resultar em corrupção de dados catastrófica.
