---
title: Heidelpay
description: Heidelpay is an internationally operating payment institution, authorized and regulated by the Federal Financial Supervisory Authority.
originalLink: https://documentation.spryker.com/v3/docs/heidelpay
originalArticleId: dad6bfb0-4a82-4eb2-9b5b-e345458389e5
redirect_from:
  - /v3/docs/heidelpay
  - /v3/docs/en/heidelpay
---

## Partner Information

[ABOUT HEIDELPAY](https://www.heidelpay.de/) 
Heidelpay is an internationally operating payment institution, authorized and regulated by the Federal Financial Supervisory Authority. The Full-Service Payment Provider covers the entire range of services connected to international electronic payment processing. For more than 13 years the company has been successfully realizing projects of online and stationary retailers and currently serves more than 16.000 customers in many different industrial sectors worldwide. 

## Integrating Heidelpay

To integrate Hidelpay in your project, follow these steps:

1. [Install](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-installation.html) Heidelpay
2. [Integrate](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-integration-into-the-legacy-demoshop.html) Heidelpay into your Legacy Demoshop project or [integrate](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-integration-into-the-legacy-demoshop.html-scos)  Heidelpay into your Spryker Commerce OS project
3. Configure selected payment methods:

  - Paypal ([Paypal Authorize](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-paypal-authorize.html),[Payal Debit](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-paypal-debit-workflow.html))
  - [Credit Card](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-credit-card-secure.html)
  - [iDeal](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-ideal.html)
  - [Easy Credit](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-easy-credit.html)
  - [Sofort](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelay-sofort-online-transfer.html)
  - [Direct Debit](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-direct-debit.html)
  - [Invoice Secured B2C](/docs/scos/dev/technology-partners/201907.0/payment-partners/heidelpay/heidelpay-invoice-secured-b2c.html)

4. Build your own workflow (create a new OMS which will use Hidelpay). See the section below for more information.

## Building a State Machine Workflow to Use Heidelpay Payment Methods

We use state machines for handling and managing orders and payments.
To use Heidelpay, [create a new OMS](http://documentation.spryker.com/v4/docs/oms-state-machine.htm) which includes necessary Heildelpay payment methods. You can use the same state machines or build new ones. The state machine commands and conditions trigger Heidelpay facade calls in order to perform the needed requests to Heidelpay API.

Some examples of the basic and fully functional state machines for each payment method were already built: `vendor/spryker-eco/heidelpay/config/Zed/Oms`

* `HeidelpaySofort01.xml`
* `HeidelpayPaypalDebit01.xml`
* `HeidelpayIdeal01.xml`
* `HeidelpaySofort01.xml`
* `HeidelpayCreditCardSecureAuthorize01.xml`
---

## Copyright and Disclaimer

See [Disclaimer](https://github.com/spryker/spryker-documentation).

---
For further information on this partner and integration into Spryker, please contact us.

<div class="hubspot-forms hubspot-forms--docs">
<div class="hubspot-form" id="hubspot-partners-1">
            <div class="script-embed" data-code="
                                            hbspt.forms.create({
				                                portalId: '2770802',
				                                formId: '163e11fb-e833-4638-86ae-a2ca4b929a41',
              	                                onFormReady: function() {
              		                                const hbsptInit = new CustomEvent('hbsptInit', {bubbles: true});
              		                                document.querySelector('#hubspot-partners-1').dispatchEvent(hbsptInit);
              	                                }
				                            });
            "></div>
</div>
</div>