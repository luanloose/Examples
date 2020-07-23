# Repeat tasks workthough

* Do more than once

```PHP
foreach ($elements as $element) {

    $this->driver->findElement(By::id('AutoCompleteProcedimento'))->sendKeys($element['Key1']);

    $this->driver->findElement(By::cssSelector('SELECTOR'))->click();

    $this->driver->findElement(By::id('ID'))
            ->sendKeys($element['Key2']);

    $this->driver->findElement(By::id('ID'))->click();
}
```

* Close modals

```PHP
$elements = $this->driver->findElements(
    By::cssSelector('img[action="closeWindow"]')
);

foreach ($elements as $element) {
    $element->click();
}
```
