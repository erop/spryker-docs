---
title: Payments feature overview
description: Orders can be paid with none, one or multiple payment methods that can be selected during checkout. Offer multiple payment methods for a single order.
originalLink: https://documentation.spryker.com/v6/docs/payments-feature-overview
originalArticleId: 0ba32e4b-d972-4eb9-ab8c-c0aafc8d1495
redirect_from:
  - /v6/docs/payments-feature-overview
  - /v6/docs/en/payments-feature-overview
---

The *Payments* feature allows your customers to pay for orders with none (for example, a [gift card](/docs/scos/dev/features/202009.0/gift-cards/gift-cards-feature-overview.html), one or multiple payment methods during the checkout process. Most orders are paid with a single payment method but in some cases, it may be useful to allow multiple payment methods. For instance, the customer may want to use two credit cards or a gift card in addition to a traditional payment method.

To make it possible, your customers to select a payment method during the checkout, you should fulfill the following conditions:

* make it active
* assign to specific stores

This can be configured in the Back Office.

The Spryker Commerce OS offers integrations with several payment providers that can be used in the checkout and order management. Easily define the availability of a provider based on customer preferences and local regulations and specify the order the providers are displayed in during checkout.

## Payment providers

The Spryker Commerce OS supports integration of the following payment providers, which are our official partners:

* [Adyen](/docs/scos/dev/technology-partners/202009.0/payment-partners/adyen/adyen.html)
* [AfterPay](/docs/scos/dev/technology-partners/202009.0/payment-partners/afterpay/afterpay.html)
* [Amazon Pay](/docs/scos/dev/technology-partners/202009.0/payment-partners/amazon-pay/amazon-pay.html)
* [Arvato](/docs/scos/dev/technology-partners/202009.0/payment-partners/arvato/arvato.html)
* [Billie](/docs/scos/dev/technology-partners/202009.0/payment-partners/billie.html)
* [Billpay](/docs/scos/dev/technology-partners/202009.0/payment-partners/billpay/billpay.html)
* [Braintree](/docs/scos/dev/technology-partners/202009.0/payment-partners/braintree/braintree.html)
* [BS Payone](/docs/scos/dev/technology-partners/202009.0/payment-partners/bs-payone/bs-payone.html)
* [Computop](/docs/scos/dev/technology-partners/202009.0/payment-partners/computop/computop.html)
* [CrefoPay](/docs/scos/dev/technology-partners/202009.0/payment-partners/crefopay/crefopay.html)
* [Heidelpay](/docs/scos/dev/technology-partners/202009.0/payment-partners/heidelpay/heidelpay.html)
* [Klarna](/docs/scos/dev/technology-partners/202009.0/payment-partners/klarna/klarna.html)
* [Payolution](/docs/scos/dev/technology-partners/202009.0/payment-partners/payolution/payolution.html)
* [Powerpay](/docs/scos/dev/technology-partners/202009.0/payment-partners/powerpay.html)
* [Ratenkauf by Easycredit](/docs/scos/dev/technology-partners/202009.0/payment-partners/ratenkauf-by-easycredit/ratenkauf-by-easycredit.html)
* [RatePay](/docs/scos/dev/technology-partners/202009.0/payment-partners/ratepay/ratepay.html)

## Dummy payment
By default, Spryker provides the [DummyPayment](https://github.com/spryker/dummy-payment) module, which has Credit Card and Invoice payments implemented. You can use these implemented payment methods, or refer to the DummyPayment modulewhen implementing additional payment methods in your project.
For details on how a new payment method is implemeted, see the articles on [how to implement the Direct Debit payment method](/docs/scos/dev/developer-guides/202009.0/development-guide/back-end/data-manipulation/payment-methods/direct-debit-example-implementation/implementing-direct-debit-payment.html). Based on the examples in these articles, you can implement other payment methods for your projects.

## Payment methods in the Back Office
In the Back Office, you can view all payment methods available in the shop application, make a payment method active (visible) or inactive (invisible) in the Payment step of the checkout process. In addition, you can define stores in which a payment method will be displayed. If changed, the payment methods will be updated in the checkout as well. 

{% info_block warningBox "Note" %}
Keep in mind that prior to managing payment methods in the Back Office, first, you need to create them by [importing payment methods data using a .CSV file](/docs/scos/dev/developer-guides/202009.0/development-guide/data-import/data-import-categories/commerce-setup/file-details-payment-method.csv.html
{% endinfo_block %}. 

![List of payment methods](https://spryker.s3.eu-central-1.amazonaws.com/docs/Features/Payment/Payment+Methods+Overview/payment-methods-list.png)

See [Managing Payment Methods](/docs/scos/user/user-guides/202009.0/back-office-user-guide/administration/payment-methods/managing-payment-methods.html) to learn more on how to make a payment method available during the checkout and assign it to different stores.



<!-- Managing Payment Methods in the Back Office

Overview of the reference information when working with payment methods in the Back Office

HowTo - Import Payment Method Store Relation Data

Hydrating payment methods for an order

  -->