---
title: 'MDVA-35910: validação de formulário interrompida quando "Logon como cliente" desativado'
description: O patch MDVA-35910 resolve o problema em que a validação do formulário de criação de conta do cliente é interrompida quando a extensão **Fazer logon como cliente** é desativada. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35910. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.
exl-id: fa63d725-33f0-4422-bcd5-d62dfee01b65
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-35910: validação de formulário interrompida quando &quot;Logon como cliente&quot; desativado

O patch MDVA-35910 resolve o problema em que a validação do formulário de criação de conta de cliente é interrompida quando a extensão **Fazer logon como cliente** é desabilitada. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19 está instalada. A ID do patch é MDVA-35910. Observe que o problema foi corrigido no Adobe Commerce versão 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce na infraestrutura em nuvem 2.4.1

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.1-2.4.2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

<u>Etapas a serem reproduzidas</u>:

1. Navegue até **Lojas > Configuração > Clientes**. Desabilitar **Logon como Cliente** no Administrador.
1. Em **Fazer logon como Cliente**, defina **Habilitar Extensão** = *Não*.
1. Salve a configuração e limpe o cache.
1. Volte para a loja e clique em **Registrar** (Criar uma conta de cliente).
1. Preencha o formulário da conta e confirme se a validação em **Confirmar email** está funcionando ou não.

<u>Resultados esperados</u>:

O processo de criação da conta do cliente é concluído sem erros.

<u>Resultados reais</u>:

O processo de criação de conta do cliente não é concluído, e os erros do console do javascript são exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) na documentação do desenvolvedor.
