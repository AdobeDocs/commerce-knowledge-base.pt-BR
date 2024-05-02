---
title: Depreciação das integrações de pagamento principais do Adobe Commerce
description: Devido à Diretiva Serviços de Pagamento PSD2 (consulte os detalhes sobre [Diretiva Serviços de Pagamento](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) em nosso guia do usuário) e à evolução contínua de muitas APIs, várias integrações de pagamento principais do Adobe Commerce correm o risco de se tornarem desatualizadas e não estarem mais em conformidade com a segurança no futuro. Para esse fim, muitas integrações de pagamento principais foram ou serão descontinuadas em breve, e recomendamos uma transição para suas extensões Commerce Marketplace correspondentes. Leia o restante do artigo abaixo para analisar as descontinuações recentes das integrações de pagamento. Cada um dos links **Status** são encontrados em nosso guia do usuário. **As integrações abaixo serão removidas da versão 2.4.0 do Adobe Commerce e foram descontinuadas das versões 2.3.**
exl-id: c2c4b3b6-409d-466f-a4f3-dfe13ac7f972
feature: Compliance, Integration
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# Depreciação das integrações de pagamento principais do Adobe Commerce

Devido à Diretiva Serviços de Pagamento PSD 2 (ver [Diretiva relativa aos serviços de pagamento](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-payment-services-directive.html) em nosso guia do usuário) e a evolução contínua de muitas APIs, várias integrações de pagamento principais do Adobe Commerce correm o risco de se tornarem obsoletas e não estarem mais em conformidade com a segurança no futuro. Para esse fim, muitas integrações de pagamento principais foram ou serão descontinuadas em breve, e recomendamos uma transição para suas extensões Commerce Marketplace correspondentes. Leia o restante do artigo abaixo para analisar as descontinuações recentes das integrações de pagamento. Cada um dos **Status** os links são encontrados em nosso guia do usuário. **As integrações abaixo serão removidas da versão 2.4.0 do Adobe Commerce e foram descontinuadas das versões 2.3.**

<table style="height: 243px;" width="712">
<tbody>
<tr>
<td style="width: 225.455px;"><strong>Integração do método de pagamento</strong></td>
<td style="width: 226.364px;"><strong>Status</strong></td>
<td style="width: 226.364px;"><strong>Recomendação do Adobe Commerce 2.X</strong></td>
</tr>
<tr>
<td style="width: 225.455px;">Pagamento mundial</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto desde a versão 2.3.5</a><br>2.4.0 - Será completamente removido</td>
<td style="width: 226.364px;">Pergunte ao seu provedor de serviços de pagamento qual solução ele recomenda para atender aos requisitos de PSD2.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto desde a versão 2.3.4</a><br>2.4.0 - Será completamente removido</td>
<td style="width: 226.364px;">Use o <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">extensão oficial</a> do Commerce Marketplace em vez disso.</td>
</tr>
<tr>
<td style="width: 225.455px;">Authorize.net (Publicação direta)</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto desde a versão 2.3.1</a><br>2.4.0 - Será completamente removido</td>
<td style="width: 226.364px;">Use o <a href="https://marketplace.magento.com/authorizenet-magento-module-authorizenet.html">extensão oficial</a> do Commerce Marketplace em vez disso.</td>
</tr>
<tr>
<td style="width: 225.455px;">CyberSource</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto desde a versão 2.3.3</a><br>2.4.0 - Será completamente removido</td>
<td style="width: 226.364px;">Use o <a href="https://marketplace.magento.com/cybersource-global-payment-management.html">extensão oficial</a> do Commerce Marketplace em vez disso.</td>
</tr>
<tr>
<td style="width: 225.455px;">Via</td>
<td style="width: 226.364px;">2.3.x - <a href="https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html?lang=en#recommended-solutions">Obsoleto desde a versão 2.3.3</a><br>2.4.0 - Será completamente removido</td>
<td style="width: 226.364px;">Pergunte ao seu provedor de serviços de pagamento qual solução ele recomenda para atender aos requisitos de PSD2.</td>
</tr>
</tbody>
</table>

**Observe que a integração do método de pagamento principal do PayPal não será descontinuada ou removida e permanecerá compatível com todas as versões 2.3.x e 2.4.x.**

## Como manter seus pagamentos seguros no futuro

Para todas as implantações de Adobe Commerce e Magento Open Source que ainda usam integrações de pagamento obsoletas, siga as recomendações abaixo, para garantir que os pagamentos de seus clientes estejam seguros, que os pagamentos não sejam recusados e para se preparar para a atualização para o Adobe Commerce 2.4.0:

* Instalar e configurar a extensão do método de pagamento oficial do [Commerce Marketplace](https://marketplace.magento.com/extensions/payments-security/payment-integration.html?_ga=2.108129217.2105547619.1564067043-238341041.1564067043) como mencionado no quadro acima.
* Desabilitar integrações de pagamento obsoletas no Administrador (definir **Ativado** opção de configuração para *Não* ) para que não apareçam mais na vitrine como opções de pagamento. Em vez disso, verifique se todos os novos pedidos são pagos por meio da integração de extensão.
* Como a nova integração do Commerce Marketplace não poderá processar transações de pagamento feitas usando uma integração de pagamento obsoleta, recomendamos usar ambos os métodos de pagamento para algum período em paralelo; mas apenas para a conclusão de transações já lançadas e possíveis reembolsos. Para fazer isso, mantenha o método de pagamento obsoleto desativado, mas deixe todos os campos de configuração preenchidos.
