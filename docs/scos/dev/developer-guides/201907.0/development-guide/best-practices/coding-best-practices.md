---
title: Coding Best Practices
description: In this article we outline a few common PHP coding problems and the recommended solutions.
originalLink: https://documentation.spryker.com/v3/docs/coding-best-practices
originalArticleId: 39862c8c-d82e-44e9-813e-7b064f48faf2
redirect_from:
  - /v3/docs/coding-best-practices
  - /v3/docs/en/coding-best-practices
---

In this article we outline a few common PHP coding problems and the recommended solutions.

## Merging Arrays

When merging arrays, one usually uses `array_merge($defaults, $options)`. However, when working with associative arrays (keys are all string identifiers), it is recommended to use the `+` operator. This is not only a lot faster, it also yields more correct results with edge cases. Beware of the switched order in this case: `$mergedOptions = $options + $defaults;`

## Operations Per Line

To facilitate readability and debugging, it is recommended to use only one operation per line.

## Method Size

Long methods tend to have too many responsibilities, and are usually harder to understand and maintain than smaller ones. Therefore it is advisable to stick to the "single responsibility" principle, when a method is just a few lines long.

 

<!-- Last review date: Nov. 22nd, 2017--  by Mark Scherer -->