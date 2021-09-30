---
title: CrefoPay - Callback
description: Callbacks are redirects performed by the CrefoPay system.
originalLink: https://documentation.spryker.com/v6/docs/crefopay-callback
originalArticleId: 34d953c5-f06b-4260-977b-95fedca5d9fb
redirect_from:
  - /v6/docs/crefopay-callback
  - /v6/docs/en/crefopay-callback
---

Callbacks are redirects performed by the CrefoPay system. The CrefoPay system redirects customers back to the URLs configured for the merchants shop. For each shop, you can define a single URL of each of the following types: confirmation, success and error.
These callbacks are used only for payment methods that redirect to a different page like PayPal.

Callback URLs can be configured in merchant back end and must have the following format:

* Confirmation URL: `http://de.mysprykershop.com/crefo-pay/callback/confirmation `
* Success URL: `http://de.mysprykershop.com/crefo-pay/callback/success`
* Failure URL: `http://de.mysprykershop.com/crefo-pay/callback/failure`