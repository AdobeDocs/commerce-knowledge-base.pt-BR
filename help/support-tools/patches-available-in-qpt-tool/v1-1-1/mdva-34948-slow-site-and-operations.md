---
title: 'MDVA-34948: Lentidão do site'
description: O patch do Adobe Commerce MDVA-34948 corrige o problema de lentidão do site. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.1 está instalada. A ID do patch é MDVA-34948. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.1.
exl-id: ba5417b3-a71c-4f1b-877b-4e7206f86660
feature: Observability, Configuration
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# MDVA-34948: Lentidão do site


## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce em nossa infraestrutura em nuvem 2.4.0-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce no local e Adobe Commerce em nossa infraestrutura em nuvem 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O site fica lento, o que dificulta as operações.

<u>Etapas a serem reproduzidas</u>:

1. Executar `show processlist` no MySQL.
1. Verifique se há várias consultas como:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>Resultados esperados</u>:

`GET_LOCK` deve ser executado imediatamente.

<u>Resultados reais</u>:

Várias consultas `GET_LOCK` ficam travadas por até 10 segundos cada.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
