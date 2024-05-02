---
title: "MDVA-38132: redirecionamento infinito quando o URL de back-end é diferente do URL do site padrão"
description: O patch MDVA-38132 corrige o problema de redirecionamento infinito quando o URL de back-end é diferente do URL de site padrão. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.25 está instalada. A ID do patch é MDVA-38132. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.
exl-id: 122145d7-0961-47f8-8ab6-a15d62996e49
feature: Cache
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-38132: Redirecionamento infinito quando o URL de back-end é diferente do URL do site padrão

O patch MDVA-38132 corrige o problema de redirecionamento infinito quando o URL de back-end é diferente do URL de site padrão. Este patch está disponível quando a variável [Ferramenta de correções de qualidade (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) O 1.0.25 está instalado. A ID do patch é MDVA-38132. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**
Adobe Commerce na infraestrutura em nuvem 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**
Adobe Commerce (todos os métodos de implantação) 2.3.3-2.4.2-p1
>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O painel Administrador do Commerce tem um redirecionamento infinito quando o URL de back-end é diferente do URL padrão do site.

<u>Pré-requisitos</u>:

* O URL base é usado para o back-end e a loja. O URL seguro de base não é usado.
* O servidor Web é configurado para que o Adobe Commerce possa ser acessado por meio de dois URLs diferentes. O URL 1 é usado para a instalação do Adobe Commerce.

<u>Etapas a serem reproduzidas</u>:

1. Ir para Painel de administração > **Lojas** > **Configuração** > **Web**.
1. Deixe o URL base original na configuração global. É o seu URL 1.
1. Alternar para o escopo do site principal.
1. Altere o URL base para um URL diferente (consulte pré-condições para configurar o servidor Web corretamente). Este é o seu URL2.
1. Limpar o cache (se necessário e possível).
1. Abra o Painel de administração.

<u>Resultados esperados</u>:

O Painel de administração foi aberto com sucesso e pode ser navegado. O armazenamento do site principal foi aberto com sucesso e pode ser navegado.

<u>Resultados reais</u>:

Ocorre um redirecionamento infinito. O Adobe Commerce redireciona do URL 1 para URL 2 e continua para frente e para trás.

## Aplicar o patch

Para aplicar patches individuais, use os seguintes links, dependendo do seu produto Adobe Commerce:

* Adobe Commerce ou Magento Open Source no local: [Guia de atualização de software > Aplicar patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://devdocs.magento.com/cloud/project/project-patch.html) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatendimento de correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de patches de qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis na ferramenta QPT, consulte o [Correções disponíveis na ferramenta QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) seção.
