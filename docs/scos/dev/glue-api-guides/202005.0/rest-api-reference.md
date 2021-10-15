---
title: REST API Reference
description: This page provides an exhaustive reference for the REST API endpoints present in Spryker by default with the corresponding parameters and data formats.
template: glue-api-storefront-guide-template
originalLink: https://documentation.spryker.com/v5/docs/rest-api-reference
originalArticleId: 59a0fb96-4694-4cb4-885e-a18b0fdab225
redirect_from:
  - /v5/docs/rest-api-reference
  - /v5/docs/en/rest-api-reference
---

This document provides an overview of REST API endpoints provided by Spryker by default. For each endpoint, you will find its URL relative to the server, REST request parameters, as well as the appropriate request and response data formats.

<div id="swagger-ui"></div>

<div class="script-link-loader" data-tag-type = "link" data-src="https://cdnjs.cloudflare.com/ajax/libs/swagger-ui/3.22.1/swagger-ui.css"></div>
<div class="script-link-loader" data-tag-type = "script" data-src="https://cdnjs.cloudflare.com/ajax/libs/swagger-ui/3.22.1/swagger-ui-standalone-preset.js"></div> 
<div class="script-link-loader" data-tag-type = "script" data-src="https://cdnjs.cloudflare.com/ajax/libs/swagger-ui/3.22.1/swagger-ui-bundle.js" ></div>


<div class="script-embed" data-code="window.onload = function() {
                console.log('start');
				const ui = SwaggerUIBundle({
					url: 'https://spryker.s3.eu-central-1.amazonaws.com/docs/Document+360/json/spryker_rest_api.schema.json',
					dom_id: '#swagger-ui',
					deepLinking: true,
					presets: [
						SwaggerUIBundle.presets.apis,
						SwaggerUIStandalonePreset
					],
                     enableCORS: false,
					layout: 'BaseLayout',
                    supportedSubmitMethods: []
				})
                console.log(ui);
				window.ui = ui
			}">
</div>

