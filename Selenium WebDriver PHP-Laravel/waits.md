# Wait workthough

## Wait for a specific element to show up

* Set the timeout to seconds, and the time in interval to ms

```PHP
$this->$driver->wait(20, 1000)->until(
        WebDriverExpectedCondition::titleIs('WebDriver Page')
        );

$this->driver->wait(3, 500)->until(
            Condition::visibilityOfElementLocated(
                By::cssSelector('li:nth-child(2) > span')
            )
        );
```

## Implicit waits

An implicit wait is to tell WebDriver to poll the DOM for a certain amount of time when trying to find an element or elements if they are not immediately available

```PHP
// set the timeout for implicit waits as 10 seconds
$driver->manage()->timeouts()->implicitlyWait = 10

$driver->get("http://somedomain/url_that_delays_loading");

$element = $driver->findElement(WebDriverBy::id('some-dynamic-element'));
```
