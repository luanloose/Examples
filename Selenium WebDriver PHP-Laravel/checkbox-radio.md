# checkbox workthough

* Checkbox/Radio

* Check if it is selected

```PHP
$this->driver->findElement(WebDriverBy::id('CheckBox'))->isSelected();
```

* Select the element

```PHP
$this->driver->findElement(WebDriverBy::id('CheckBox'))->click();
```

* Deselect the element

```PHP
$this->driver->findElement(WebDriverBy::id('CheckBox'))->clears();
```
