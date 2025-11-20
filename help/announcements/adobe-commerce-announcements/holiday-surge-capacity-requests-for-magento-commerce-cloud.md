---
title: Solicitações de capacidade de aumento temporário do Adobe Commerce em nossa infraestrutura em nuvem
description: Durante a temporada de pico de vendas de feriados (aproximadamente de meados de novembro a meados de janeiro), a Adobe recomenda que todos os comerciantes da Adobe Commerce hospedados em nossa infraestrutura em nuvem se preparem para aumentar o tráfego.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: 9cd7eeb6af379fa94e234bb677b532051079995c
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Solicitações de capacidade de aumento temporário do Adobe Commerce em nossa infraestrutura em nuvem

Durante a temporada de pico de vendas de feriados (aproximadamente de meados de novembro a meados de janeiro), a Adobe recomenda que todos os comerciantes da Adobe Commerce hospedados em nossa infraestrutura em nuvem se preparem para aumentar o tráfego.

Para obter uma lista de verificação abrangente entre soluções e práticas recomendadas para preparar seus sistemas e equipes para a temporada de pico, consulte o [Guia do Adobe DX Unified Holiday Readiness](https://experienceleague.adobe.com/pt-br/docs/support-resources/data-sheets/unified-holiday-readiness).

**Planejando e estimando o tráfego**

Recomendamos que todos os comerciantes da Adobe Commerce em nossa infraestrutura em nuvem [utilizem esse conjunto de recomendações sobre como estimar o tráfego da temporada de pico](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) para a temporada de pico de vendas das festas a cada ano.

Depois de concluir a estimativa recomendada, se sua equipe tiver identificado datas em que você acha que precisará de capacidade adicional, continue para a próxima etapa para obter informações sobre como solicitar capacidade de sobretensão.

**Exibir o histórico de seus uploads**

Você pode exibir o histórico de redimensionamentos solicitados solicitando as informações do seu **CSM (Customer Success Manager)**.
As seguintes informações estão disponíveis para cada solicitação de redimensionamento:

* **Data de Início do Tamanho**: data da solicitação de upsize.
* **Data de Término do Tamanho**: data em que o cluster retornou ao tamanho anterior.
* **Tamanho do vCPU**: o tamanho do cluster após o upsize.
* **Dias de Uso**: por quantos dias o cluster ficou com upsizing.
* **Period vCPU**: tamanho de vCPU alterado pelo número de dias em que foi usado. (por exemplo, o tamanho do vCPU 192 por 25 dias é igual a 4.800).

**Solicitando Capacidade de Sobretensão**

Os comerciantes da Adobe Commerce em nossa infraestrutura em nuvem que antecipam a necessidade de capacidade adicional durante a temporada de festas devem [enviar um Tíquete de Suporte para Capacidade Excedida](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html?lang=pt-BR) por meio de nossa [Central de Ajuda](/help/overview.md), indicando as datas e as necessidades de capacidade esperadas dentro do tíquete. Observe que o aumento da capacidade exigirá o uso da capacidade excedente licenciada.

**Recomendamos o envio desses tíquetes com pelo menos 48 horas úteis de antecedência em relação à necessidade da capacidade. Além disso, recomendamos que as solicitações referentes ao período Black Friday/Cyber Monday sejam feitas com a maior antecedência possível, já que a capacidade durante esse período é limitada.**


**Mais Ajuda?**

Precisa de mais orientação sobre como se preparar para o tráfego de pico de temporada? Os comerciantes da Adobe Commerce em nossa infraestrutura em nuvem podem entrar em contato com a equipe de conta da Adobe para obter ajuda, estratégia e dicas de planejamento para se preparar para uma temporada de pico bem-sucedida. Também recomendamos consultar o [Blog do Magento](https://magento.com/blog) para obter dicas de estratégia o ano todo.

## Recursos para analisar sua capacidade

Em nossa base de conhecimento de suporte:

* [Cálculo de alocação de CPU para Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html?lang=pt-BR)
* [Verifique se o upsize das instâncias do host é necessário para o Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html?lang=pt-BR)
* [Verificar a configuração do CPU do host para o Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html?lang=pt-BR)
* [Identificar e medir interrupções do Adobe Commerce na nuvem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html?lang=pt-BR)
