---
title: 'MDVA-43201: erro ao usar o campo DOB com PT de localidade'
description: O patch MDVA-43201 resolve o problema em que ocorre um erro ao usar o atributo do cliente DOB no formulário de registro do cliente para a localidade portuguesa. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-43201. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: erro ao usar o campo DOB com PT de localidade

O patch MDVA-43201 resolve o problema em que ocorre um erro ao usar o atributo do cliente DOB no formulário de registro do cliente para a localidade portuguesa. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10 está instalada. A ID do patch é MDVA-43201. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando o atributo DOB customer é adicionado ao formulário de registro do cliente para localidade portuguesa, o formulário fornece o erro *Argument 1 passado para iterator_to_array() must implement interface travesable, null given*.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados.

<u>Etapas a serem reproduzidas</u>:

1. Acesse Admin > **Lojas** > **Configuração** > **Geral** > **Opções de Localidade**, defina a Localidade como **Português (Portugal)** e clique em **Salvar**.
1. Reindexe e limpe o cache.
1. Vá para **Lojas** > **Atributo** > **Cliente**.
1. Abra o atributo de cliente DOB e defina **Mostrar na Loja** como **Sim**.
1. Selecione tudo de **Formulário a ser usado em**.
1. Salve o atributo.
1. Acesse a página Criar nova conta no front-end.

<u>Resultados esperados</u>:

O formulário de registro do cliente da loja portuguesa não fornece nenhum erro ao adicionar o atributo DOB.

<u>Resultados reais</u>:

O formulário de registro do cliente da loja portuguesa fornece um erro ao adicionar o atributo DOB.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) na documentação do desenvolvedor.
