---
title: Heidelpay - Sofort (Online Transfer)
description: Integrate Sofort payment through Heidelpay into the Spryker-based shop.
originalLink: https://documentation.spryker.com/2021080/docs/heidelpay-sofort
originalArticleId: ac896fad-2456-4d4e-a590-6d970b8a6e97
redirect_from:
  - /2021080/docs/heidelpay-sofort
  - /2021080/docs/en/heidelpay-sofort
  - /docs/heidelpay-sofort
  - /docs/en/heidelpay-sofort
---

## Setup

The following configuration should be made after Heidelpay has been [installed](/docs/scos/dev/technology-partners/{{page.version}}/payment-partners/heidelpay/heidelpay-installation.html) and [integrated](/docs/scos/dev/technology-partners/{{page.version}}/payment-partners/heidelpay/scos-integration/heidelpay-integration-into-scos.html).

## Configuration

Example (for testing only):
```php
$config[HeidelpayConstants::CONFIG_HEIDELPAY_TRANSACTION_CHANNEL_SOFORT] = '31HA07BC8142C5A171749CDAA43365D2';
```

## Checkout Payment Step Display
Displays payment method name with radio button. No extra input fields are required.

## Payment Step Submitting
No extra actions needed, quote being filled with payment method selection as default.

## Workflow
### Summary Review and Order
 Submit

<u>On "save order" event</u> - save Heidelpay payment, per order and items, as usual

<u>When state machine is initialized</u>, an event "send authorize request" will trigger the authorize request. In case of success, payment system will return a redirect URL for customer where the payment can be completed. Request and response will be fully persisted in the database (`spy_payment_heidelpay_transaction_log`). 

<u>On "post save hook" event</u>, we check in the transaction log table, if the authorize request was sent successful, and if so, we set external redirect response (URL is obtained from the previous step) and redirect customer to the Sofort webiste, where customer confirms the payment. <br>
Below is the code sample from `HeidelpayPostSavePlugin`:
```php
/**
 * @method \SprykerEco\Zed\Heidelpay\Business\HeidelpayFacadeInterface getFacade()
 * @method \SprykerEco\Zed\Heidelpay\Business\HeidelpayBusinessFactory getFactory()
 */
class HeidelpayPostSavePlugin extends BaseAbstractPlugin implements CheckoutPostCheckPluginInterface
{
 /**
 * @param \Generated\Shared\Transfer\QuoteTransfer $quoteTransfer
 * @param \Generated\Shared\Transfer\CheckoutResponseTransfer $checkoutResponseTransfer
 *
 * @return void
 */
 public function execute(QuoteTransfer $quoteTransfer, CheckoutResponseTransfer $checkoutResponseTransfer)
 {
 $this->getFacade()->postSaveHook($quoteTransfer, $checkoutResponseTransfer);
 }
}
```

<u>On payment confirmation</u>, response is sent to the Heidelpay and Heidelpay makes an asynchronous POST request to the shop's `CONFIG_HEIDELPAY_PAYMENT_RESPONSE_URL` URL (Yves), with the result of payment (see `HeidelpayController::paymentAction()`). This is called "external response transaction", the result will be persisted in `spy_payment_heidelpay_transaction_log` as usual.

The most important data here - is the payment reference ID which can be used for further transactions like capture/cancel/etc. 

In the response Heidelpay expects an URL string which defines where customer has to be redirected. In case if customer successfully confirmed payment, it should be link to checkout order success step, in case of failure - checkout payment failed action with error code (see `HeidelpayController::paymentFailedAction()` and [Heidelpay - Workflow for Errors](/docs/scos/dev/technology-partners/{{page.version}}/payment-partners/heidelpay/technical-details-and-howtos/heidelpay-workflow-for-errors.html) section). Heidelpay redirects customer to the given URL and payment process is finished. 

Now order can be considered as "paid", no further capture is needed.