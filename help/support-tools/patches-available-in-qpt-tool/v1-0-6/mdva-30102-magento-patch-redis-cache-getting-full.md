---
title: "MDVA-30102: Cache Redis ficando cheio"
description: O patch MDVA-30102 resolve o problema do cache Redis ficar cheio e gerar erros, causando problemas com as Páginas de listagem de produtos (PLP) e Páginas de detalhes do produto (PDP), como a falta de produtos. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 está instalada.
exl-id: 34772296-8c93-471c-b5ad-6815adb78ca6
feature: Cache, Categories, Services
role: Admin
source-git-commit: 324cce66df1e4ab7ec4ef8fb6512c3acbabdf3ab
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-30102: Cache Redis ficando cheio

O patch MDVA-30102 resolve o problema do cache Redis ficar cheio e gerar erros, causando problemas com as Páginas de listagem de produtos (PLP) e Páginas de detalhes do produto (PDP), como a falta de produtos. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.6 está instalada.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cache Redis está ficando cheio, e o `maxmemory` alocado parece ser insuficiente. O cache de layout não tinha TTL e não foi removido, causando o crescimento do cache e a remoção de outras chaves no Redis. Como resultado, toda a memória Redis era alocada para cache de layout.

<u>Pré-requisitos</u>:

* O usuário deve usar o Adobe Commerce 2.4 e ter 100.000 produtos simples (o tipo de produto não importa) e 50 categorias.
* O cache Redis deve ser configurado de acordo com as etapas fornecidas em [Guia de Configuração do Adobe Commerce > Usar Redis para a página do Adobe Commerce e cache padrão](https://devdocs.magento.com/guides/v2.4/config-guide/redis/redis-pg-cache.html#example-command) na documentação do desenvolvedor.

<u>Etapas a serem reproduzidas</u>:

1. Navegue por todos os PDPs e PLPs. Você pode usar o [OWASP ZAP](https://www.zaproxy.org/) para rastrear o site.
1. Observe o uso de memória Redis.
1. Além disso, verifique a configuração atual e a memória usada. Execute o seguinte comando na CLI. Ele verifica a memória usada, maxmemory, chaves removidas e o tempo de atividade do Redis em dias:

```
redis-cli -p REDIS_PORT -h REDIS_HOST info | egrep --color "(role|used_memory_peak|maxmemory|evicted_keys|uptime_in_days)"
```

<u>Resultados esperados</u>:

O cache Redis não deve estar crescendo rapidamente.

<u>Resultados reais</u>:

O cache Redis cresce até ~5 GB. Há um limite máximo de 8 GB de memória Redis, portanto, se você tiver produtos de 1 M, rapidamente ficará sem memória.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
