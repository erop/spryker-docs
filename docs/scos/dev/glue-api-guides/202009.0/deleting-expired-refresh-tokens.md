---
title: Deleting expired refresh tokens
description: Delete expired refresh tokens by setting their lifetime or manually.
originalLink: https://documentation.spryker.com/v6/docs/deleting-expired-refresh-tokens
originalArticleId: 5072fd16-8f0d-4fa8-a033-985eee38e1f5
redirect_from:
  - /v6/docs/deleting-expired-refresh-tokens
  - /v6/docs/en/deleting-expired-refresh-tokens
---

After an authentication refresh token is [revoked](/docs/scos/dev/glue-api-guides/{{page.version}}/authentication-and-authorization.html) or expires, it remains in the database.

For security reasons and to reduce the database storage space, we recommend deleting the tokens by setting their liftime. Once they have a lifetime, you can configure a cron job to delete them automatically or do it manually.


To configure the lifetime of refresh tokens, [extend](/docs/scos/dev/back-end-development/extending-spryker/extending-the-spryker-core-functionality.html) the `Spryker\Shared\Oauth\OauthConfig` class on a project level.

To configure the [cron job](/docs/scos/dev/sdk/202009.0/cronjob-scheduling.html) to delete the tokens with expired lifetime, configure the time interval for the job via the `Spryker\Shared\Oauth\OauthConfig::getRefreshTokenRetentionInterval()` method.

To delete the tokens with expired lifetime manually, run the command:
```bash
vendor/bin/console oauth:refresh-token:remove-expired
```


