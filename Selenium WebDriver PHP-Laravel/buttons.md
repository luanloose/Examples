# Buttons workthough

* Simple click in a Button/Link/Image

```PHP
$element = $this->driver->findElement(WebDriverBy::id('BUTTON_ID'))->click();
```

* When you have only part of a button text

```PHP
$elements = $this->driver->findElements(By::cssSelector('SELECTOR'));

foreach ($elements as $element) {

    $botao = $element->GetAttribute("innerText");

    if ($botao === "TEXT") {
        $element->click();
            break;
        }
    }
```
