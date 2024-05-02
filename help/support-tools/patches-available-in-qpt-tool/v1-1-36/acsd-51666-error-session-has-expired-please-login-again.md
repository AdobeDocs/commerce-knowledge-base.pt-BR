---
title: 'ACSD-51666: Erro "A sessão expirou, faça logon novamente". depois de fazer logon'
description: Aplique o patch ACSD-51666 para corrigir o problema do Adobe Commerce em que o erro *A sessão expirou. Faça logon novamente.* ocorre depois que você tenta fazer logon.
feature: Customers
role: Admin, Developer
exl-id: c3913f1c-f401-440b-b6b3-10702f13fff5
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-51666: erro *A sessão expirou. Faça logon novamente.* depois de fazer logon

O patch ACSD-51666 corrige o problema em que o erro *A sessão expirou. Faça logon novamente.* ocorre depois que você tenta fazer logon. Este patch está disponível quando a variável [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) O 1.1.36 está instalado. A ID do patch é ACSD-51666. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Você recebe o erro *A sessão expirou. Faça logon novamente.* ao tentar fazer login com a nova senha de um dispositivo depois de redefinir a senha em outro dispositivo. Isso só acontece se houver uma solicitação adicional do Ajax na página adicionada por um módulo personalizado.

<u>Etapas a serem reproduzidas</u>:

1. Instale um módulo personalizado que adicione uma solicitação de Ajax em cada página da loja.
1. Crie uma nova conta.
1. Faça logoff e volte para a página de logon.
1. Abra o *Esqueceu a senha* vincule em um navegador diferente e envie o *Redefinir senha* email.
1. Abra o email de redefinição de senha no primeiro navegador e defina a nova senha.
1. Tente fazer logon no segundo navegador.

<u>Resultados esperados</u>:

Você pode fazer logon com êxito na primeira tentativa.

<u>Resultados reais</u>:

* Você vê a *A sessão expirou. Faça logon novamente.* erro.
* Você não está conectado e não é redirecionado para a página inicial.
* A segunda tentativa de logon foi bem-sucedida.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
