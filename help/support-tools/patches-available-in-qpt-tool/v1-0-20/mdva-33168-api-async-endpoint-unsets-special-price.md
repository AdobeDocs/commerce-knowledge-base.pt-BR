---
title: "MDVA-33168: O endpoint assíncrono da API cancela a definição do preço especial"
description: O patch MDVA-33168 corrige o problema em que o uso do endpoint assíncrono da API para atualizar um atributo de produto cancela a definição de um preço especial.
exl-id: 4dd26215-b140-4924-8f4d-0d062e5fda2d
feature: REST, Orders, Personalization
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-33168: O endpoint assíncrono da API cancela a definição do preço especial

O patch MDVA-33168 corrige o problema em que o uso do endpoint assíncrono da API para atualizar um atributo de produto cancela a definição de um preço especial.

Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20 está instalada. A ID do patch é MDVA-33168. Observe que o problema está planejado para ser corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.3.3-p1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem e Adobe Commerce no local 2.3.3 - 2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites com lojas.
1. Acesse **Lojas > Configurações > Catálogo > Catálogo > Preço > Catálogo** e Defina **Escopo de Preço** = *Site*.
1. Criar um atributo de produto *tipo-texto*. Deixe todas as opções como padrão.
1. Adicione o atributo criado ao conjunto de atributos padrão.
1. Crie um produto simples para usar com um produto de pacote.
1. Crie um produto de pacote com as seguintes opções de Exemplo:
   * **Habilitar Produto** = *Sim*.
   * **Conjunto de Atributos** = *Padrão*.
   * **Nome do Produto** = *bundle-1*.
   * **SKU** = *bundle-1*.
   * **SKU Dinâmica** = *Sim*.
   * **Preço** = *$100,00*.
   * **Classe de Imposto** = *Mercadorias Tributáveis*.
   * **Status do Estoque** = *No Estoque*.
1. Em **Itens do Pacote**, defina estas opções de Exemplo:
   * **Enviar Itens do Pacote** = *Juntos*.
   * **Título da Opção** = *teste*, **Tipo de Entrada** = *Botões de Opção*, **Obrigatório** caixa de seleção = *marcado*.
   * **É Padrão** caixa de seleção = *desmarcado*.
   * **Nome** = *simple-100*.
   * **SKU** = *simple-100*.
   * **Preço** = *100.00*.
   * **Tipo de Preço** = *Fixo*.
   * **Quantidade Padrão** = *1*.
   * **Caixa de seleção Definida pelo Usuário** = *desmarcada*.
1. Alterne o escopo para o armazenamento não padrão e defina o preço especial. (Exemplo: na página **Advanced Pricing**, defina **Special Price** = *4%*, e **Price View** = *Price Range*.)
1. Atualize o novo atributo somente no escopo de armazenamento não padrão, como neste Exemplo:

   ```php
       PUT {{base_url}}/rest/en_au/async/V1/products/{{sku}}    {        "product": {            "custom_attributes": [                {                    "attribute_code": "text_attr",                    "value": 21                                   }            ]                    }    }
   ```

<u>Resultados esperados</u>:

Outros valores de atributo permanecem os mesmos ao atualizar um atributo de produto usando a API rest assíncrona, conforme esperado.

<u>Resultados reais</u>:

O preço especial, que foi definido usando a API rest assíncrona no escopo da loja, é removido.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte os [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
