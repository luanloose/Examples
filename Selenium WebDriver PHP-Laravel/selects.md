# Selects workthough

* Get the select element

```PHP
$select = $driver->findElement(WebDriverBy::tagName('select'));
```

* Get all the options for this element

```PHP
$allOptions = $select->findElement(WebDriverBy::tagName('option'));
```

* Select the options

```PHP
foreach ($allOptions as $option) {
  echo "Value is:" . $option->getAttribute('value');
  $option->click();
}
```

* select normal

```PHP
$select = new Select($this->driver->findElement(By::id("ID")));
$select->selectByVisibleText("PALAVRA");
```

* select com parte do texto

```PHP
$select = new Select($this->driver->findElement(
            By::id('ID')
        ));
$options = $select->getOptions();

foreach ($options as $elemento) {
    $texto = $elemento->getText();
    if (strstr($texto, "PALAVRA")) {
         $select->selectByVisibleText($texto);
        break;
    }
}
```
