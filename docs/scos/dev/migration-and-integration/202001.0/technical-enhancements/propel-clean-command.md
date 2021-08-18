---
title: Propel Clean Command
description: Learn how to integrate the Propel clean command into your project.
originalLink: https://documentation.spryker.com/v4/docs/propel-clean-command
originalArticleId: 06bfaaf1-e436-4d73-9b0e-b5cdf4bc1393
redirect_from:
  - /v4/docs/propel-clean-command
  - /v4/docs/en/propel-clean-command
---

The `propel:database:drop` command is used to clean a database of all the tables, indexes, counters and so on. The command invokes the `drop` process to delete and re-create the database from scratch. 

When working with a remote database, you might have insufficient permissions to invoke the `drop` process. To cover the case, the `vendor/bin/console propel:tables:drop` command was introduced. The command cleans the database without dropping it. 

## Integration

### Install Feature Core

#### Prerequisites

Ensure that the related features are installed:

| Name | Version | Required sub-feature |
| --- | --- | --- |
| Spryker Core | 201907.0 | [Feature](/docs/scos/dev/migration-and-integration/202001.0/feature-integration-guides/spryker-core-feature-integration.html) |

#### 1)Install the Required Modules Using Composer

Run the following command(s) to install the required modules:

```bash
composer require spryker/propel:"^3.10.0" --update-with-dependencies
```

{% info_block warningBox "Verification" %}

Make sure that the following module has been installed:

| Module | Expected Directory |
| --- | --- |
|  `Propel ` |  `vendor/spryker/propel ` |

{% endinfo_block %}

#### 2) Set Up Behavior

Clean up codeception configuration by deleting  `SetupHelper ` from all codeception configuration files:

```shell
- \SprykerTest\Shared\Application\Helper\SetupHelper
```

{% info_block infoBox %}
Use  `SprykerTest\Shared\Testify\Helper\DataCleanupHelper ` instead to clean up data after each test that can intersect with other tests.
{% endinfo_block %}

Enable the  `DatabaseDropTablesConsole ` console command in  `Pyz\Zed\Console\ConsoleDependencyProvider `:

src/Pyz/Zed/Console/ConsoleDependencyProvider.php

```php
    <?php
    class ConsoleDependencyProvider extends SprykerConsoleDependencyProvider
{
    /**
     * @param \Spryker\Zed\Kernel\Container $container
     *
     * @return \Symfony\Component\Console\Command\Command[]
     */
    protected function getConsoleCommands(Container $container)
    {
        $commands = [
            ...
            new DatabaseDropTablesConsole(),
            ...
```

{% info_block infoBox %}
* Spryker\Zed\Propel\Communication\Console\DatabaseExportConsole is deprecated.
{% endinfo_block %}
{% info_block infoBox %}
* Spryker\Zed\Propel\Communication\Console\DatabaseImportConsole is deprecated.
{% endinfo_block %}

Run  `vendor/bin/console ` and make sure the  `propel:tables:drop ` command is in the list.