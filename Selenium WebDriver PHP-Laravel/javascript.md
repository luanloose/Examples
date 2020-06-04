# Javascript workthough

## Execute javascript

```PHP
$this->driver->executeScript("return window.location.pathname");
```

```PHP
$this->driver->executeScript('document.getElementById("quantidadeProcedimento").value = "' . $elemento['amount'] . '";');
```

```PHP
$this->driver->executeScript('window.open("RedirectRegulacaoTiss.asp","_self","");');
```

```PHP
$this->driver->executeScript("document.querySelector(" . "\"input[name='QUANTIDADE']\").value = '" . $elemento['amount'] . "' ;");
```

```PHP
$this->driver->executeScript('function(null);');
```
