---
title: CMS Extension Points
description: The CMS module provides an extension point for post activation and deactivation of CMS pages.
originalLink: https://documentation.spryker.com/v4/docs/cms-extension-points
originalArticleId: 50c717c3-4f0d-4da4-94fe-374c7290757b
redirect_from:
  - /v4/docs/cms-extension-points
  - /v4/docs/en/cms-extension-points
---

The CMS module provides an extension point for post activation and deactivation of CMS pages. The plugin interface set for this extension point is as follows:

```php
<?php

namespace Spryker\Zed\Cms\Communication\Plugin;

use Generated\Shared\Transfer\CmsPageTransfer;

interface PostCmsPageActivatorPluginInterface
{
    /**
     * Specification:
     * - Runs after the CMS activator class functions (activate and deactivate)
     *
     * @api
     *
     * @param \Generated\Shared\Transfer\CmsPageTransfer $cmsPageTransfer
     *
     * @return void
     */
    public function execute(CmsPageTransfer $cmsPageTransfer);
}
```

For example, Navigation is connected with activation and deactivation of CMS pages, so there is a plugin in the `CmsNavigationConnector` module that is called `PostCmsPageActivatorNavigationPlugin`.

It implements the interface as follows:

```php
<?php

namespace Spryker\Zed\CmsNavigationConnector\Communication\Plugin;

use Generated\Shared\Transfer\CmsPageTransfer;
use Spryker\Zed\Cms\Communication\Plugin\PostCmsPageActivatorPluginInterface;
use Spryker\Zed\Kernel\Communication\AbstractPlugin;

/**
 * @method \Spryker\Zed\CmsNavigationConnector\Business\CmsNavigationConnectorFacadeInterface getFacade()
 * @method \Spryker\Zed\CmsNavigationConnector\Communication\CmsNavigationConnectorCommunicationFactory getFactory()
 */
class PostCmsPageActivatorNavigationPlugin extends AbstractPlugin implements PostCmsPageActivatorPluginInterface
{
    /**
     * @param \Generated\Shared\Transfer\CmsPageTransfer $cmsPageTransfer
     *
     * @return void
     */
    public function execute(CmsPageTransfer $cmsPageTransfer)
    {
        $this->getFacade()->updateCmsPageNavigationNodesIsActive($cmsPageTransfer);
    }
}
```

And then in the `CmsDependencyProvider`, in the function `getCmsPagePostActivatorPlugins`, you can register this plugin (or any plugin implementing the above interface) for it to execute post activation or deactivation of CMS pages.