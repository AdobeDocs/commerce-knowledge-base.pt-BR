---
title: "MDVA-39384: Não é possível salvar o atributo de cliente personalizado para o usuário da empresa"
description: O patch MDVA-39384 resolve o problema em que o atributo de cliente personalizado de um usuário da empresa não é salvo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2 está instalada. A ID do patch é MDVA-39384. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384: Não é possível salvar atributo de cliente personalizado para usuário da empresa

O patch MDVA-39384 resolve o problema em que o atributo de cliente personalizado de um usuário da empresa não é salvo. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.2 está instalado. A ID do patch é MDVA-39384. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O atributo personalizado do cliente para um usuário da empresa não é salvo.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Ir para **Lojas** > Configurações > **Configuração** > **Recursos B2B** e defina o **Ativar empresa** para Sim.
1. Criar um atributo de cliente personalizado:
   * Valores Obrigatórios: Sim (opcional, ative-o para que o erro de validação seja exibido).
   * Mostrar na Loja: Sim.
   * Forms para uso no: todos disponíveis na lista.
1. Crie uma Empresa e faça logon como administrador da empresa.
1. Navegue até Estrutura da empresa na sua conta.
1. Clique no link **Adicionar usuário** link.
1. Preencha o formulário, incluindo o atributo personalizado.
1. Clique em **Salvar**.

<u>Resultados esperados</u>:

Os valores de atributo personalizados são salvos com o novo usuário da empresa.

<u>Resultados reais</u>:

Os valores de atributos personalizados NÃO são salvos com o novo usuário da empresa.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
