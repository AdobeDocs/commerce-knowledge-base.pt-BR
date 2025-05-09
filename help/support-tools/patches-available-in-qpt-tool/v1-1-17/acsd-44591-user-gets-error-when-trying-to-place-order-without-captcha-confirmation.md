---
title: 'ACSD-44591: erros ao fazer pedido sem confirmação CAPTCHA'
description: O patch ACSD-44591 resolve o problema em que o usuário recebe erros ao tentar fazer um pedido sem a confirmação CAPTCHA.
exl-id: 5459aa14-dcba-474d-aafa-e4cc73daafbc
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-44591: erros ao fazer pedido sem confirmação CAPTCHA

O patch ACSD-44591 resolve o problema em que o usuário recebe erros ao tentar fazer um pedido sem a confirmação CAPTCHA.
Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17 está instalada. A ID do patch é ACSD-44591. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário recebe erros ao tentar fazer um pedido sem confirmação CAPTCHA.

<u>Etapas a serem reproduzidas</u>:

1. Configure o Google ReCaptcha v2 (eu não sou um robô).
1. Ative o ReCaptcha para check-out.
1. Tente fazer um pedido sem clicar no ReCaptcha.
1. Depois que você receber a mensagem de erro de ReCaptcha ausente (*Falha na validação de ReCaptcha, tente novamente*), clique em **ReCaptcha** e tente fazer um pedido.

<u>Resultados esperados</u>:

O pedido não será feito com o ReCaptcha incorreto.

<u>Resultados reais</u>:

Você recebe os seguintes erros:

* Falha na validação de *ReCaptcha. Tente novamente*
* *Não existe esse carrinho com id = 1*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) na documentação do desenvolvedor.
