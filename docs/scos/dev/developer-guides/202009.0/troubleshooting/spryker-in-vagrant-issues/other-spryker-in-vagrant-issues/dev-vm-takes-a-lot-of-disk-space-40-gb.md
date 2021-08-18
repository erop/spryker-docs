---
title: Dev VM takes a lot of disk space (40+ GB)
description: Learn how to fix the issue when Dev VM takes a lot of disk space (40+ GB)
originalLink: https://documentation.spryker.com/v6/docs/dev-vm-takes-a-lot-of-disk-space-40-gb
originalArticleId: bcc5b063-a692-43ef-87c0-775246b24f3d
redirect_from:
  - /v6/docs/dev-vm-takes-a-lot-of-disk-space-40-gb
  - /v6/docs/en/dev-vm-takes-a-lot-of-disk-space-40-gb
---

## Description

Spryker Virtual Machine creates a dynamically allocated storage that grows over time as you add data. However, if you delete the data from the virtual machine later, you'll notice that the disk doesn't automatically shrink.

## Solution
To solve this issue, you can use the [dd](https://en.wikipedia.org/wiki/Dd_(Unix)) utility. To do this, run the following commands inside the folder where you placed the source code (by default, it's *devvm*):

```bash
vagrant up
vagrant ssh -c 'sudo dd if=/dev/zero of=/EMPTY bs=1M; sudo rm -f /EMPTY; sudo sync'
```
