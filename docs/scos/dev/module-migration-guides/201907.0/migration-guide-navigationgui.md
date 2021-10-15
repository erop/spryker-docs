---
title: Migration Guide - NavigationGui
template: module-migration-guide-template
originalLink: https://documentation.spryker.com/v3/docs/mg-navigation-gui
originalArticleId: bdb7d2e0-a89e-4186-8306-e9b58c0670b3
redirect_from:
  - /v3/docs/mg-navigation-gui
  - /v3/docs/en/mg-navigation-gui
---

## Upgrading from Version 1.* to Version 2.*

In version 2, validity dates allow to preset date boundaries for each navigation node to control their own and their descendants visibility.

* Upgrade Navigation module to at least 2.0.0 version. See [Migration Guide - Navigation](/docs/scos/dev/module-migration-guides/{{page.version}}/migration-guide-navigation.html) to learn how to migrate the `Navigation` module.
* Update the NavigationGui module to at least 2.0.0 version in your `composer.json`.
* Make sure the new Zed user interface assets are built by running `npm run zed` (or `antelope build zed` for older versions).

Now, validity dates will be stored in Storage. 

To apply validity dates on navigation node display, take a look on Navigation feature integration.

<!-- Last review date: Sep 21, 2017 by Karoly Gerner -->