---
title: Integrating Prepayment into Checkout
description: This article describes how to integrate prepayment into Checkout.
originalLink: https://documentation.spryker.com/v5/docs/ht-prepayment-checkout
originalArticleId: 5d5f3be3-31d1-4c54-99bf-4ec0aef0428e
redirect_from:
  - /v5/docs/ht-prepayment-checkout
  - /v5/docs/en/ht-prepayment-checkout
---

The next step is to integrate prepayment into `Checkout`. In the `PaymentMethods/Dependency/Injector` from Yves add the `CheckoutDependencyInjector` that will inject the prepayment form and handler into the `Checkout` module:

<details open>
<summary>Code sample:</summary>
    
```php
<?php

namespace Pyz\Yves\PaymentMethods\Dependency\Injector;

use Spryker\Shared\Kernel\ContainerInterface;
use Spryker\Shared\Kernel\Dependency\Injector\DependencyInjectorInterface;
use Spryker\Yves\Checkout\CheckoutDependencyProvider;
use Pyz\Yves\PaymentMethods\Plugin\PrepaymentHandlerPlugin;
use Pyz\Yves\PaymentMethods\Plugin\PrepaymentSubFormPlugin;
use Spryker\Yves\StepEngine\Dependency\Plugin\Form\SubFormPluginCollection;
use Spryker\Yves\StepEngine\Dependency\Plugin\Handler\StepHandlerPluginCollection;
use Pyz\Shared\PaymentMethods\PaymentMethodsConstants;

class CheckoutDependencyInjector implements DependencyInjectorInterface
{
    /**
     * @param \Spryker\Shared\Kernel\ContainerInterface|\Spryker\Yves\Kernel\Container $container
     *
     * @return \Spryker\Shared\Kernel\ContainerInterface|\Spryker\Yves\Kernel\Container
     */
    public function inject(ContainerInterface $container)
    {
        $container = $this->injectPaymentSubForms($container);
        $container = $this->injectPaymentMethodHandler($container);

        return $container;
    }

    /**
     * @param \Spryker\Shared\Kernel\ContainerInterface $container
     *
     * @return \Spryker\Shared\Kernel\ContainerInterface
     */
    protected function injectPaymentSubForms(ContainerInterface $container)
    {
        $container->extend(static::PAYMENT_SUB_FORMS, function (SubFormPluginCollection $paymentSubForms) {
            $paymentSubForms->add(new PrepaymentSubFormPlugin());

            return $paymentSubForms;
        });

        return $container;
    }

    /**
     * @param \Spryker\Shared\Kernel\ContainerInterface $container
     *
     * @return \Spryker\Shared\Kernel\ContainerInterface
     */
    protected function injectPaymentMethodHandler(ContainerInterface $container)
    {
        $container->extend(static::PAYMENT_METHOD_HANDLER, function (StepHandlerPluginCollection $paymentMethodHandler) {
            $paymentMethodHandler->add(new PrepaymentHandlerPlugin(), PaymentMethodsConstants::PROVIDER);

            return $paymentMethodHandler;
        });

        return $container;
    }
}
```

</br>
</details>

{% info_block errorBox %}
If you re-created this example in Demoshop, you’ll need to do some adjustments on the selectPayment(
{% endinfo_block %} from `checkout.js`.)