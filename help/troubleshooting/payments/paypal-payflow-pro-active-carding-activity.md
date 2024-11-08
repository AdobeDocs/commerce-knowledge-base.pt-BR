---
title: Atividade de cartão ativa do PayPal Payflow Pro
description: ATUALIZADO EM 2 DE abril DE 2019
exl-id: 9fe73788-5b67-445a-9b0d-86489125d271
feature: Cache, Orders, Payments
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '665'
ht-degree: 0%

---

# Atividade de cartão ativa do PayPal Payflow Pro

ATUALIZADO EM 2 DE abril DE 2019

A integração PayPal Payflow Pro no Adobe Commerce está sendo ativamente alvo da atividade de cartões, onde os invasores tentam centenas de transações de US$ 0 com cartões de crédito roubados para verificar a validade do cartão.

A atividade atualmente segmenta as versões dessa integração do Payflow Pro que foram incluídas no Adobe Commerce 2.1.x, 2.2.x, 2.3.x para Magento Open Source e Commerce (no local e na nuvem). A atividade de cartão é inerente à forma como o Payflow Pro é integrado nos carrinhos de compras.

>[!NOTE]
>
>Para ajudar a resolver esses problemas, fornecemos novos pacotes do Composer para adicionar o Google reCAPTCHA ou CAPTCHA ao formulário de finalização do Payflow Pro. Recomendamos instalar esses pacotes em todas as versões e edições do Adobe Commerce.

O problema afeta as seguintes versões do Adobe Commerce:

* Adobe Commerce no local v2.1.x, 2.2.x, 2.3.x
* Adobe Commerce na infraestrutura em nuvem v2.1.x, 2.2.x, 2.3.x

## Problema

Os sintomas desses ataques incluem:

* Sua conta PayPal Payflow Pro mostra centenas de transações fraudulentas identificadas
* O PayPal pode suspender uma conta do Payflow Pro devido a transações de fraude recebidas e cobrar taxas substanciais

## Solução

Para ajudar a proteger contra esses ataques, recomendamos adicionar o Google reCAPTCHA (recomendado) ou CAPTCHA ao formulário de finalização do Payflow Pro. Isso inclui a instalação dos pacotes do Composer e a configuração do Google reCAPTCHA ou CAPTCHA no Commerce Admin.

### Instalar pacotes

O Adobe criou duas opções de pacote para adicionar o Google reCAPTCHA e/ou CAPTCHA ao formulário de finalização do Payflow Pro. A instalação de um desses pacotes atualizará as instalações atuais e adicionará uma opção que pode ajudar a melhorar essa segurança no formulário de checkout do Payflow Pro.

Esses pacotes são compatíveis com as seguintes implantações e versões do Adobe Commerce:

Adobe Commerce (todos os métodos de implantação) e Magento Open Source 2.1.x, 2.2.x, 2.3.x

A instalação requer comandos da CLI para a instância do Adobe Commerce. Pode ser necessária a assistência do desenvolvedor.

>[!NOTE]
>
>Recomendamos instalar e configurar o Google reCAPTCHA, além de instalar quaisquer atualizações relevantes do formulário de checkout do Payflow Pro. Essa opção fornece uma verificação invisível e várias opções de configuração.

#### Instalar o Google reCAPTCHA e fazer check-out das atualizações do formulário

O pacote `magento/module-paypal-recaptcha` contém integração com atualizações de formulário de pagamento do Google reCAPTCHA e Payflow Pro. Mesmo que você tenha o módulo reCAPTCHA instalado e configurado, recomendamos instalar este pacote.

Execute os seguintes comandos para instalá-lo.

**Para Adobe Commerce local:**

```bash
composer require magento/module-paypal-recaptcha
bin/magento module:enable Magento_PaypalReCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Para o Adobe Commerce na infraestrutura em nuvem:**

1. Execute o seguinte comando:

   ```bash
   composer require magento/module-paypal-recaptcha
   ```

1. Confirmar e enviar alterações:

   ```bash
   git add -A && git commit -m "Install Google reCAPTCHA"    git push origin %branch_name%
   ```

1. Aguarde a conclusão da implantação.

#### Instalar atualizações do formulário de check-out para CAPTCHA

O pacote `magento/module-paypal-captcha` contém integração com o módulo CAPTCHA nativo do Adobe Commerce.

Execute os seguintes comandos para instalá-lo:

**Para Adobe Commerce local:**

```bash
composer require magento/module-paypal-captcha
bin/magento module:enable Magento_PaypalCaptcha
bin/magento setup:upgrade
bin/magento cache:clean
```

**Para o Adobe Commerce na infraestrutura em nuvem:**

1. Execute o seguinte comando:

   ```bash
   composer require magento/module-paypal-captcha
   ```

1. Confirmar e enviar alterações:

   ```bash
   git add -A && git commit -m "Install CAPTCHA"    git push origin %branch_name%
   ```

1. Aguarde a conclusão da implantação.

### Configurar o Google reCAPTCHA ou CAPTCHA

Após instalar o pacote, configure o Google reCAPTCHA (recomendado) ou CAPTCHA conforme descrito nos seguintes documentos:

* [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha) em nosso guia do usuário.
* [CAPTCHA](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-captcha) em nosso guia do usuário.

A nova opção de formulário de check-out é:

* Google reCAPTCHA: usar no formulário de pagamento do PayPal Payflow Pro
* CAPTCHA: Fluxo de pagamento Pro

## Suporte e contatos do PayPal

Entre em contato com o Suporte ao comerciante do PayPal Payflow para saber mais sobre os Serviços de Proteção contra Fraude. Você pode solicitar que a equipe de Suporte do PayPal habilite os [Serviços Básicos de Proteção contra Fraude](https://developer.paypal.com/api/nvp-soap/payflow/fraud-protection/) para fornecer o controle mais rígido possível sobre os pagamentos, de modo que você possa negar automaticamente os pagamentos que provavelmente resultarão em transações fraudulentas e aceitar pagamentos que normalmente não são um problema. Observe que após ativar os filtros de Serviços de Proteção contra Fraude do PayPal, as transações podem levar até 2 horas para serem liquidadas.

>[!NOTE]
>
>Adobe Para obter informações adicionais, consulte a Base de Dados de Conhecimento [&quot;do PayPal, que me contatou sobre minha integração com o Payflow Pro. O que preciso fazer?&quot;](https://www.paypal.com/us/smarthelp/article/ts2242).

**Detalhes de Suporte ao Comerciante do PayPal Payflow**

O horário comercial do Suporte ao comerciante de Fluxo de Pagamento é de segunda a sexta-feira, das 7h às 20h CST. Você pode entrar em contato com o Suporte ao comerciante do Payflow para obter assistência da conta por telefone ou email:

* Telefone: 1-888-883-9770 (selecione o prompt 2)
* Clientes internacionais: 1-408-967-0191
* Email: [payflow-support@paypal.com](mailto:payflow-support@paypal.com)

Suporte à Austrália

* De segunda a sexta das 8h às 19h (horário da Austrália)
* Telefone: +61 2 8288 0198
* Email: [gateway-ausupport@paypal.com](mailto:gateway-ausupport@paypal.com)
