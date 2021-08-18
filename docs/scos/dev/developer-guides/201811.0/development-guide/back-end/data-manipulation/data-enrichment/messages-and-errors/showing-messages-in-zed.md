---
title: Showing Messages in Zed
description: This article describes how to show a message in the Zed GUI.
originalLink: https://documentation.spryker.com/v1/docs/flash-messenger
originalArticleId: 3795459e-66b8-42c9-8169-a6fcc6a712a7
redirect_from:
  - /v1/docs/flash-messenger
  - /v1/docs/en/flash-messenger
---

This article describes how to show a message in the Zed GUI.

In the controller you can use these shortcut methods to show a user message in the GUI. The messages will be translated later when they are rendered.


```php
<?php
class IndexController extends AbstractController
{
    public function indexAction()
    {
        $this->addSuccessMessage($message);
 
        $this->addInfoMessage($message);
 
        $this->addErrorMessage($message);
    }
}
```

## Show Message from Zed’s Business Layer
To show a message from a model, declare this dependency in the module’s dependency provider:

Now, you can access it from the business factory and inject it to your model:

```php
<?php
class MyBundleBusinessFactory extends AbstractBusinessFactory
{
    public function createAnyModel()
    {
        return new AnyModel(
            $this->getFlashMessengerFacade()
        );
    }
 
    protected function getFlashMessengerFacade()
    {
        return $this->getProvidedDependency(GlossaryDependencyProvider::FACADE_FLASH_MESSENGER);
    }
}
```

And finally, use it in your model:

```php
<?php
class AnyModel
{
    protected $flashMessengerFacade;
 
 
    public function __construct(FlashMessengerFacade $flashMessengerFacade)
    {
        $this->flashMessengerFacade = $flashMessengerFacade;
    }
 
    public function doSomething()
    {
        $this->flashMessengerFacade->addInfoMessage('Hello world!');
    }
}
```