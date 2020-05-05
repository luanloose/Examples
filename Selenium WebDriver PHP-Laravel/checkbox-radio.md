# checkbox workthough

* Checkbox/Radio

* Check if it is selected

```PHP
$driver->findElement(WebDriverBy::id('CheckBox'))->isSelected();
```

* Select the element

```PHP
$driver->findElement(WebDriverBy::id('CheckBox'))->click();
```

* Deselect the element

```PHP
$driver->findElement(WebDriverBy::id('CheckBox'))->clears();
```
