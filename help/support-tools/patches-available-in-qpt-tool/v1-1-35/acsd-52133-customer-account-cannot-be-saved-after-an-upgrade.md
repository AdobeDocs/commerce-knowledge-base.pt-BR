---
title: "ACSD-52133: a conta do cliente não pode ser salva após uma atualização"
description: Aplique o patch ACSD-52133 para corrigir o problema do Adobe Commerce em que uma conta de cliente não pode ser salva após uma atualização.
feature: Customers, Upgrade
role: Admin
exl-id: 0db7c79e-10e1-4850-81b5-4812fb051941
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-52133: A conta do cliente não pode ser salva após uma atualização

O patch ACSD-52133 corrige o problema em que uma conta de cliente não pode ser salva após uma atualização. Este patch está disponível quando a variável [!DNL Quality Patches Tool (QPT)] O 1.1.35 está instalado. A ID do patch é ACSD-52133. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch é criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com novos [!DNL Quality Patches Tool] versões. Para verificar se o patch é compatível com sua versão do Adobe Commerce, atualize o `magento/quality-patches` pacote para a versão mais recente e verifique a compatibilidade no [[!DNL Quality Patches Tool]: Página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A conta do cliente não pode ser salva após uma atualização.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce versão 2.4.4.
1. Crie um cliente.
1. Atualize o Adobe Commerce para 2.4.6 a partir da versão anterior da 2.4.4, na qual um cliente já foi criado.
1. Defina a chave de criptografia conforme abaixo em `env.php`:

   `d337b914e91ff703b1e94ba4156aadf0`

1. Defina os valores abaixo no banco de dados para qualquer cliente sob o `customer_entity` tabela:

   ```
   -> rp_token as incr4869
   -> rp_token_created_at as "2021-04-29 20:06:14"
   ```

1. Ir para **[!UICONTROL Admin]** > **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Edite o cliente para o qual os valores acima foram atualizados.
1. Clique em **[!UICONTROL Save Customer]** ou **[!UICONTROL Save and Continue Edit]**

<u>Resultados esperados</u>:

O cliente foi salvo com sucesso sem erros.

<u>Resultados reais</u>:

* O registro do cliente não foi salvo.
* O administrador vê a seguinte mensagem de erro: *Ocorreu um problema ao salvar o cliente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no [!DNL Quality Patches Tool] guia.
* Adobe Commerce na infraestrutura em nuvem: [Upgrades e Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançado: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no [!DNL Quality Patches Tool] guia.
