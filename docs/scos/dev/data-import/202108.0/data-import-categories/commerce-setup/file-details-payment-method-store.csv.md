---
title: File details- payment_method_store.csv
last_updated: Jun 16, 2021
template: data-import-template
originalLink: https://documentation.spryker.com/2021080/docs/file-details-payment-method-storecsv
originalArticleId: c862d612-e933-43dd-afce-27dbc5a0ba37
redirect_from:
  - /2021080/docs/file-details-payment-method-storecsv
  - /2021080/docs/en/file-details-payment-method-storecsv
  - /docs/file-details-payment-method-storecsv
  - /docs/en/file-details-payment-method-storecsv
---

This article contains content of the **payment_method_store.csv** file to configure Payment Method Store information on your Spryker Demo Shop.

## Headers & Mandatory Fields 
These are the header fields to be included in the .csv file:

| Field Name | Mandatory | Type | Other Requirements/Comments | Description |
| --- | --- | --- | --- | --- |
| **payment_method_key** | Yes | String |Value should be imported from the [payment_method.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/commerce-setup/file-details-payment-method.csv.html) file. | Identifier of the payment method. |
| **store** | Yes | String | Value must be within an existing store name, set in the *store.php* configuration file of the demo shop PHP project. | Name of the store. |
*N/A: Not applicable.

## Dependencies

This file has the following dependencies:
*     [payment_method.csv](/docs/scos/dev/data-import/{{page.version}}/data-import-categories/commerce-setup/file-details-payment-method.csv.html) 
*     *stores.php* configuration file of the demo shop PHP project

## Template File & Content Example
A template and an example of the *payment_method_store.csv*  file can be downloaded here:

| File | Description |
| --- | --- |
| [payment_method_store.csv template](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/Template+payment_method_store.csv) | Payment Method Store .csv template file (empty content, contains headers only). |
| [payment_method_store.csv](https://spryker.s3.eu-central-1.amazonaws.com/docs/Developer+Guide/Back-End/Data+Manipulation/Data+Ingestion/Data+Import/Data+Import+Categories/Commerce+Setup/payment_method_store.csv) | Payment Method Store .csv file containing a Demo Shop data sample. |
