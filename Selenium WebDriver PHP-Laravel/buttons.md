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

* If you have problems try this

```PHP
$action = new Action($this->driver);
$botao = $this->driver->findElement(By::xpath("(//button[@type='button'])[15]"));
$action->moveToElement($botao)->click()->perform();
```
