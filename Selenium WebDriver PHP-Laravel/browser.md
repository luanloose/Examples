# Webdriver workthough

* Open a browser ( I like chrome )

```PHP
// Silent mode
$host = 'http://localhost:4444/wd/hub';

$desiredCapabilities = DesiredCapabilities::chrome();
$desiredCapabilities->setCapability(
    'goog:chromeOptions',
    ['args' => [
        '--disable-gpu',
        '--headless',
        '--no-sandbox',
        'window-size=1024,768'
        ]]
);

return RemoteWebDriver::create($host, $desiredCapabilities);

// Window Mode
$host = 'http://localhost:4444/wd/hub';

$desiredCapabilities = DesiredCapabilities::chrome();
$desiredCapabilities->setCapability(
    'goog:chromeOptions',
    ['args' => [
        'no-first-run',
        'window-size=1024,768'
    ]]
);

return RemoteWebDriver::create($host, $desiredCapabilities);
```

* Go to a specified URL

```PHP
$this->driver->get('http://google.com');
$this->driver->navigate()->to('http://google.com');
```

> 'NOTE' -- the WebDriver may not wait for the page to load, you'd better using explicit and implicit waits.
