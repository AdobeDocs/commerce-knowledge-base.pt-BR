---
title: "MDVA-43201: Erro ao usar o campo DOB com PT de localidade"
description: O patch MDVA-43201 resolve o problema em que ocorre um erro ao usar o atributo do cliente DOB no formulário de registro do cliente para a localidade portuguesa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-43201. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: erro ao usar o campo DOB com PT de localidade

O patch MDVA-43201 resolve o problema em que ocorre um erro ao usar o atributo do cliente DOB no formulário de registro do cliente para a localidade portuguesa. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.10 está instalado. A ID do patch é MDVA-43201. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando o atributo do cliente DOB é adicionado ao formulário de registro do cliente para localidade em português, o formulário fornece o erro *Argumento 1 passado para iterator_to_array() deve implementar interface travesable, null dado*.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Ir para Admin > **Lojas** > **Configuração** > **Geral** > **Opções de localidade**, defina a localidade como **Português (Portugal)** e clique em **Salvar**.
1. Reindexe e limpe o cache.
1. Ir para **Lojas** > **Atributo** > **Cliente**.
1. Abrir atributo do cliente DOB e definir **Mostrar na vitrine** para **Sim**.
1. Selecionar tudo de **Formulário a ser usado em**.
1. Salve o atributo.
1. Acesse a página Criar nova conta no front-end.

<u>Resultados esperados</u>:

O formulário de registro do cliente da loja portuguesa não fornece nenhum erro ao adicionar o atributo DOB.

<u>Resultados reais</u>:

O formulário de registro do cliente da loja portuguesa fornece um erro ao adicionar o atributo DOB.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
