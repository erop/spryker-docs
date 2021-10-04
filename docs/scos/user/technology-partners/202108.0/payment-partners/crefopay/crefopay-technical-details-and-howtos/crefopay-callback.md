---
title: CrefoPay - Callback
description: Callbacks are redirects performed by the CrefoPay system.
originalLink: https://documentation.spryker.com/2021080/docs/crefopay-callback
originalArticleId: 620ac3f8-81fc-4aa3-b8a4-cc489dad20b5
redirect_from:
  - /2021080/docs/crefopay-callback
  - /2021080/docs/en/crefopay-callback
  - /docs/crefopay-callback
  - /docs/en/crefopay-callback
---

Callbacks are redirects performed by the CrefoPay system. The CrefoPay system redirects customers back to the URLs configured for the merchants shop. For each shop, you can define a single URL of each of the following types: confirmation, success and error.
These callbacks are used only for payment methods that redirect to a different page like PayPal.

Callback URLs can be configured in merchant back end and must have the following format:

* Confirmation URL: `http://de.mysprykershop.com/crefo-pay/callback/confirmation `
* Success URL: `http://de.mysprykershop.com/crefo-pay/callback/success`
* Failure URL: `http://de.mysprykershop.com/crefo-pay/callback/failure`