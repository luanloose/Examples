# Selects workthough

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
