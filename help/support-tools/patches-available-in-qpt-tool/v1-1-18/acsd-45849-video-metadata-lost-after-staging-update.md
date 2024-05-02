---
title: "ACSD-45849: os metadados de vídeo são perdidos após a atualização de preparo"
description: O patch ACSD-45849 corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18 está instalada. A ID do patch é ACSD-45849. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.
exl-id: 071a535d-f96c-4731-a17c-0b7bf8a87372
feature: Staging, Page Content
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-45849: os metadados de vídeo são perdidos após a atualização de preparo

O patch ACSD-45849 corrige o problema em que os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.18 está instalado. A ID do patch é ACSD-45849. Observe que o problema foi corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os metadados de vídeo são perdidos após a aplicação de uma atualização de preparo.

<u>Etapas a serem reproduzidas</u>:

1. Configure a chave de API do YouTube no **Admin** > **Lojas** > **Configuração** > **Catálogo** > **Vídeo do produto**.
1. Crie um produto com um vídeo do YouTube. Observe que o URL, o título e a descrição estão preenchidos.
1. Criar uma nova atualização agendada para o produto com qualquer parâmetro sem alterar o *Imagens e vídeo* seção.
1. Clique em **Exibir/Editar** em Alterações agendadas.
1. Ir para **Imagens e vídeos** e clique no vídeo.

<u>Resultados esperados</u>:

O URL, o título e a descrição contêm dados apropriados.

<u>Resultados reais</u>:

Os campos URL, title e description estão vazios.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
