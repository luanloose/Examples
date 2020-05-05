# Inputs workthough

* input with search dropdown

```PHP
$this->driver->findElement(By::id('busca-codigo-cbo'))
            ->sendKeys($cbo);

$element = $this->driver->findElement(By::id('ui-id-1'));

$this->driver->wait(10, 1000)->until(
            Condition::visibilityOf($element));

$this->driver->findElement(By::cssSelector('a.ui-corner-all'))->click();
```

* Input para mudar o valor via script

```PHP
$this->driver->executeScript("document.querySelector("."\"input[name='NAME']\").value = '". $value ."' ;");
```

* Input some text

```PHP
$this->driver->findElement(By::id('busca-codigo-cbo'))
            ->sendKeys($cbo);
```

* Send keyboard actions, press `cmd+a` & `delete`

```PHP
$this->driver->findElement(By::id('busca-codigo-cbo'))
              ->sendKeys(array(
                WebDriverKeys::COMMAND, // Use control on non-mac computers.
                'a',
              ));

$this->driver->findElement(By::id('busca-codigo-cbo'))
              ->sendKeys(array(
                WebDriverKeys::BACKSPACE,
              ));
```

* Clear a input

```PHP
$this->driver->findElement(By::id('busca-codigo-cbo'))
            ->clear();
```
