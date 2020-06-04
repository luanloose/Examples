# Alerts workthough

* Get the alert

```PHP
$a = $this->$driver->switchTo->alert();
```

* Accept an Alert

```PHP
$this->driver->switchTo()->alert()->accept();
```

* Decline

```PHP
$this->driver->switchTo()->alert()->dismiss();
```

* Get text

```PHP
$this->driver->switchTo()->alert()->getText();
```
