---
title: Migration Guide - Security
description: Use the guide to perform the Security part of the Silex Migration Effort.
originalLink: https://documentation.spryker.com/v5/docs/migration-guide-security
originalArticleId: 9db7fb10-c141-4e63-89af-4d1891bd7cf3
redirect_from:
  - /v5/docs/migration-guide-security
  - /v5/docs/en/migration-guide-security
---

{% info_block errorBox %}

This migration guide is a part of the [Silex migration effort](/docs/scos/dev/migration-concepts/silex-replacement/silex-replacement.html).

{% endinfo_block %}

To upgrade the module, do the following:

1. Update the module using composer:
```bash
composer require spryker/security
```
2. Remove the old service providers, if you have them in the project:
```php
\Silex\Provider\RememberMeServiceProvider
\Silex\Provider\SecurityServiceProvider
\SprykerShop\Yves\AgentPage\Plugin\Provider\AgentPageSecurityServiceProvider
\SprykerShop\Yves\CustomerPage\Plugin\Provider\CustomerSecurityServiceProvider
\SprykerShop\Yves\ShopApplication\Plugin\Provider\YvesSecurityServiceProvider
```
3. Enable new plugins in the corresponding files:

**Yves Integration**

```php
<?php

namespace Pyz\Yves\ShopApplication;


use Spryker\Yves\Security\Plugin\Application\SecurityApplicationPlugin;
use SprykerShop\Yves\ShopApplication\ShopApplicationDependencyProvider as SprykerShopApplicationDependencyProvider;

class ShopApplicationDependencyProvider extends SprykerShopApplicationDependencyProvider
{
    /**
     * @return \Spryker\Shared\ApplicationExtension\Dependency\Plugin\ApplicationPluginInterface[]
     */
    protected function getApplicationPlugins(): array
    {
        return [
            ...
            new SecurityApplicationPlugin(),
            ...
        ];
    }
}
```

4. Wire the additional plugins:

**View Details**

```php
<?php

namespace Pyz\Yves\Security;

use Spryker\Yves\Security\Plugin\Security\RememberMeSecurityPlugin;
use Spryker\Yves\Security\SecurityDependencyProvider as SprykerSecurityDependencyProvider;
use SprykerShop\Yves\AgentPage\Plugin\Security\AgentPageSecurityPlugin;
use SprykerShop\Yves\CustomerPage\Plugin\Security\CustomerPageSecurityPlugin;

class SecurityDependencyProvider extends SprykerSecurityDependencyProvider
{
    /**
     * @return \Spryker\Shared\SecurityExtension\Dependency\Plugin\SecurityPluginInterface[]
     */
    protected function getSecurityPlugins(): array
    {
        return [
            new RememberMeSecurityPlugin(),
            new AgentPageSecurityPlugin(),
            new CustomerPageSecurityPlugin(),
        ];
    }
}
```