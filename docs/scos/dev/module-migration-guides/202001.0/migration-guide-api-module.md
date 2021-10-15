---
title: Migration Guide - API Module
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v4/docs/mg-api-module
originalArticleId: 014e1eac-aec2-4b10-8ad0-d37c9320a0ca
redirect_from:
  - /v4/docs/mg-api-module
  - /v4/docs/en/mg-api-module
---

## Upgrading from Version 0.1.5 to Version 0.2.0

Version 0.2.0 of the Api module introduces a default behavior to disable legacy Zed API for security reasons.
Some projects actively use and develop Zed API. To continue using legacy Zed API, one has to override the method `isApiEnabled` of the `ApiConfig` class in your project implementation:

1. Create a new class `ApiConfig` in Pyz and extend the base class:

src/Pyz/Zed/Api/ApiConfig.php

```php
namespace Pyz\Zed\Api;

use Spryker\Zed\Api\ApiConfig as SprykerApiConfig;

class ApiConfig extends SprykerApiConfig
{
}
```
    
2. Override `isApiEnabled`  method and return true:

```php

namespace Pyz\Zed\Api;
 
use Spryker\Zed\Api\ApiConfig as SprykerApiConfig;
 
class ApiConfig extends SprykerApiConfig
{
    /**
     * @return bool
     */
    public function isApiEnabled(): bool
    {
        return true;
    }
}
```

3. Check that API is available again.