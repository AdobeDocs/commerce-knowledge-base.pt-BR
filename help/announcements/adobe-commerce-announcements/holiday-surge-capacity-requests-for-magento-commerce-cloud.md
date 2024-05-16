---
title: Solicitações de capacidade de aumento temporário do Adobe Commerce em nossa infraestrutura em nuvem
description: Durante a temporada de pico de vendas de feriados (aproximadamente de meados de novembro a meados de janeiro), a Adobe recomenda que todos os comerciantes da Adobe Commerce hospedados em nossa infraestrutura em nuvem se preparem para aumentar o tráfego.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Solicitações de capacidade de aumento temporário do Adobe Commerce em nossa infraestrutura em nuvem

Durante a temporada de pico de vendas de feriados (aproximadamente de meados de novembro a meados de janeiro), a Adobe recomenda que todos os comerciantes da Adobe Commerce hospedados em nossa infraestrutura em nuvem se preparem para aumentar o tráfego.

**Planejamento e estimativa de tráfego**

Recomendamos que todos os comerciantes do Adobe Commerce em nossa infraestrutura em nuvem [utilizar esse conjunto de recomendações sobre como estimar o tráfego da estação de pico](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) para a temporada de pico de vendas de feriados a cada ano.

Depois de concluir a estimativa recomendada, se sua equipe tiver identificado datas em que você acha que precisará de capacidade adicional, continue para a próxima etapa para obter informações sobre como solicitar capacidade de sobretensão.

**Visualizar o histórico dos uploads**

Você pode visualizar o histórico dos redimensionamentos solicitados solicitando as informações de seu **CSM (Customer Success Manager, Gerente de sucesso do cliente)**.
As seguintes informações estão disponíveis para cada solicitação de redimensionamento:

* **Data de início do tamanho**: data da solicitação de upsize.
* **Data de término do tamanho**: data em que o cluster retornou ao tamanho anterior.
* **Tamanho do vCPU**: o tamanho do cluster após o upsize.
* **Dias de uso**: por quantos dias o cluster permaneceu com upsizing.
* **Período vCPU**: tamanho do vCPU alterado de acordo com o número de dias em que foi usado. (por exemplo, o tamanho do vCPU 192 por 25 dias é igual a 4.800).

**Solicitando capacidade de sobretensão**

Os comerciantes da Adobe Commerce em nossa infraestrutura em nuvem que antecipam a necessidade de capacidade adicional durante a temporada de festas devem [Enviar um tíquete de suporte à capacidade de sobretensão](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) por meio de [Centro de ajuda](/help/overview.md), indicando as datas e as necessidades de capacidade esperadas no ticket. Observe que o aumento da capacidade exigirá o uso da capacidade excedente licenciada.

**Recomendamos enviar esses tíquetes com pelo menos 48 horas úteis de antecedência em relação à necessidade de capacidade; além disso, recomendamos que as solicitações para o período Black Friday / Cyber Monday sejam feitas com a maior antecedência possível, já que a capacidade durante esse período é limitada.**


**Mais ajuda?**

Precisa de mais orientação sobre como se preparar para o tráfego de pico de temporada? Os comerciantes da Adobe Commerce em nossa infraestrutura em nuvem podem entrar em contato com a equipe de conta da Adobe para obter ajuda, estratégia e dicas de planejamento para se preparar para uma temporada de pico bem-sucedida. Também recomendamos que você verifique o [Blog Magento](https://magento.com/blog) para dicas de estratégia o ano todo.

## Recursos para analisar sua capacidade

Em nossa base de conhecimento de suporte:

* [Cálculo de alocação de CPU para o Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [Verifique se o upsize das instâncias do host é necessário para o Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [Verifique a configuração da CPU do host para o Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [Identificar e medir paralisações do Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
