---
title: 'ACSD-52906: Resolvendo problema de cookie X-Magento-Vary para cache de cliente conectado'
description: Aplique o patch ACSD-52906 para corrigir o problema do Adobe Commerce em que o cookie X-Magento-Vary é definido incorretamente para clientes conectados.
feature: Cache
role: Admin, Developer
exl-id: 863e0808-9208-467d-8d56-9dd7a7f4354d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# ACSD-52906: Resolvendo problema de cookie X-Magento-Vary para clientes conectados

O patch ACSD-52906 corrige o problema em que o cookie X-Magento-Vary é definido incorretamente para clientes conectados. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.36 está instalado. A ID do patch é ACSD-52906. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O cookie X-Magento-Vary é definido incorretamente para clientes conectados que pertencem ao mesmo segmento do cliente, causando cache inadequado para algumas páginas.

<u>Pré-requisitos</u>:

Os módulos Adobe Commerce Inventory management (MSI) são instalados e ativados.

<u>Etapas a serem reproduzidas</u>:

1. Configure o cache [!DNL Varnish] ou [!DNL Fastly].
1. Crie um novo segmento de cliente e atribua-o aos clientes *Registrados*.
1. Crie dois clientes, por exemplo, customer1 e customer2.
1. Limpe o cache.
1. Faça logon como customer1 e vá para a página inicial.
1. Abra uma página incógnita no navegador.
1. Vá para qualquer página diferente da página inicial.
1. Faça logon como customer2.
1. Vá para a home page.
1. Verifique se a página está armazenada em cache no console de desenvolvimento do navegador.

<u>Resultados esperados</u>:

A página é recuperada do cache.

<u>Resultados reais</u>:

A página não está armazenada em cache.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] versão: uma nova ferramenta para autoatender patches de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
