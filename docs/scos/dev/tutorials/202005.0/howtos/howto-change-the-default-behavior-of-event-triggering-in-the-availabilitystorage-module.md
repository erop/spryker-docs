---
title: HowTo - Change the Default Behavior of Event Triggering in the AvailabilityStorage Module
description: Learn how to change the default behavior of the event being triggered in the AvailabilityStorage module when the amount of product is changed.
originalLink: https://documentation.spryker.com/v5/docs/ht-change-default-behaviour-of-event-trigerring-in-availability-storage-module
originalArticleId: fe5f1645-1614-4315-9c60-b1eec0d67e0d
redirect_from:
  - /v5/docs/ht-change-default-behaviour-of-event-trigerring-in-availability-storage-module
  - /v5/docs/en/ht-change-default-behaviour-of-event-trigerring-in-availability-storage-module
---

By default, events are triggered when product status is changed from `available` to `not available` and vice versa. If you want to change this behavior for the events to be triggered when the amount of product changes, follow the steps below. 

1. Remove `value="0"` and `operator="==="` from the line `<parameter name="spy_availability_abstract_quantity" column="quantity" value="0" operator="==="/>` in `src/Pyz/Zed/Availability/Persistence/Propel/Schema/spy_availability.schema.xml`:

```xml
<table name="spy_availability_abstract">
        <behavior name="event>
            <parameter name="spy_availability_abstract_quantity" column="quantity"/>
       </behavior>
</table>
```

2. Run the commands:

```bash
console propel:schema:copy
console propel:model:build
```