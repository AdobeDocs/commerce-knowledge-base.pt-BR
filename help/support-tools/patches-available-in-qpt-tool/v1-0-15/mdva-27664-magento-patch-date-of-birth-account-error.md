---
title: "Correção MDVA-27664: erro da data da conta de nascimento"
description: O patch MDVA-27664 resolve o problema em que a data de nascimento de uma conta de cliente pode ser maior do que hoje.
exl-id: c669764e-b4a5-4031-92ac-1156755e9a0a
feature: Customer Service
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Correção MDVA-27664: erro da data da conta de nascimento

O patch MDVA-27664 resolve o problema em que a data de nascimento de uma conta de cliente pode ser maior do que hoje.

Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.15 está instalado. Observe que o problema foi corrigido no Adobe Commerce versão 2.3.6.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador.
1. Definir **Localidade** = *en\_GB* (UK) para um usuário.
1. Editar um cliente.
1. Selecione uma data de nascimento após o dia 12 de um mês deste ano.

<u>Resultados esperados</u>:

A data de nascimento é válida, portanto, as informações do cliente podem ser salvas, conforme esperado.

<u>Resultados reais</u>:

As informações do cliente não podem ser salvas porque ocorre um erro de validação:

```php
The Date of Birth should not be greater than today.
```

onde, em vez do formato de data DD/MM/AAAA, a data é tratada como o formato de data MM/DD/AAAA.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte o [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) seção.
