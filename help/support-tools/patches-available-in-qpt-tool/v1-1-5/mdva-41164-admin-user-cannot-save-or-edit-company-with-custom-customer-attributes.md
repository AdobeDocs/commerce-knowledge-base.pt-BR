---
title: 'MDVA-41164: não é possível salvar ou editar a Empresa com atributos personalizados do cliente'
description: O patch MDVA-41164 resolve o problema em que o usuário administrador não pode salvar ou editar uma empresa com atributos personalizados do cliente de arquivos ou imagens de qualquer tipo. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalada. A ID do patch é MDVA-41164. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
exl-id: 24338895-68b4-404c-bedd-46cfc7e983a0
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-41164: não é possível salvar ou editar a Empresa com atributos personalizados do cliente

O patch MDVA-41164 resolve o problema em que o usuário administrador não pode salvar ou editar uma empresa com atributos personalizados do cliente de arquivos ou imagens de qualquer tipo. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.5 está instalada. A ID do patch é MDVA-41164. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode salvar ou editar uma empresa com atributos personalizados do cliente de arquivos ou imagens de qualquer tipo.

<u>Pré-requisitos</u>:

O módulo B2B está instalado.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar Empresa em **Lojas** > **Config** > **Recursos B2B**.
1. Crie um atributo de cliente em **Lojas** > **Atributos** > **Clientes** > **Adicionar novo atributo**:
   * Tipo de entrada: Arquivo (anexo)
   * Mostrar na Loja: Sim
   * Ordem de classificação: Qualquer
   * Forms para uso em: selecionar tudo
1. Crie uma nova empresa em **Clientes** > **Empresas** > **Adicionar nova empresa** e carregue um arquivo para o novo atributo criado acima.

<u>Resultados esperados</u>:

O usuário pode concluir a criação da empresa e o anexo é carregado sem erros.

<u>Resultados reais</u>:

* Você recebe uma mensagem de erro: *Algo deu errado ao salvar o arquivo.*
* O log de exceções contém um registro como o seguinte:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [Guia de Atualização de Software > Aplicar Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) na documentação do desenvolvedor.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) na documentação do desenvolvedor.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) em nossa base de dados de conhecimento de suporte.
* [Verifique se o patch está disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
