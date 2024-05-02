---
title: "Patch MDVA-34192: não é possível modificar a data dos clientes em determinado formato"
description: O patch MDVA-34192 corrige o problema em que é impossível modificar/especificar a data de nascimento do cliente usando o formato dd/mm/aaaa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.16 está instalada. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 8aa36970-b2bf-43f8-ba8f-bfc144f8d4ab
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Correção MDVA-34192: não é possível modificar a data dos clientes em determinado formato

O patch MDVA-34192 corrige o problema em que é impossível modificar/especificar a data de nascimento do cliente usando o formato dd/mm/aaaa. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.0.16 está instalado. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:** Adobe Commerce na infraestrutura em nuvem 2.3.5-p1

**Compatível com as versões do Adobe Commerce:** 2.3.4-2.3.6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O patch resolve vários problemas. A seguir estão a descrição e as etapas para reproduzir para uma delas.

O filtro de grade de produto não funciona corretamente quando filtramos usando o atributo de data personalizado e a localidade do usuário administrador é en\_GB.

<u>Etapas a serem reproduzidas:</u>:

1. Crie um usuário administrador cujo **Localidade da interface** está definida como *Inglês (Reino Unido)*.
1. Crie um atributo de data com a seguinte configuração:
   * **Tipo de Entrada de Catálogo para o Proprietário da Loja**: *Data*
   * **Usar em Opções de Filtro**: *Sim*
   * **Adicionar às Opções de Coluna**: *Sim*
1. Atribua o atributo a um conjunto de atributos.
1. Vá para a página de edição do produto, selecione uma data para o novo atributo usando o seletor de datas e salve.
1. Tente filtrar a grade de produtos usando o novo atributo de data.

<u>Resultado esperado:</u>:

O filtro de produto funciona corretamente para um atributo de data personalizado quando a localidade do usuário administrador é en\_GB.

<u>Resultado real:</u>:

O filtro de produto não funciona corretamente para um atributo de data personalizado quando a localidade do usuário administrador é en\_GB.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
