# Webdriver workthough

* Open a browser ( I like chrome )

```PHP
// Silent mode
$options = (new ChromeOptions)->addArguments([
                '--disable-gpu',
                '--headless',
                '--no-sandbox'
            ]);

$host = 'http://localhost:4444/wd/hub';

return RemoteWebDriver::create($host, DesiredCapabilities::chrome()->setCapability(
                ChromeOptions::CAPABILITY,
                $options
            ));

// Window Mode
$chromeOptions = new ChromeOptions();
$chromeOptions->addArguments(['no-first-run']);
$capabilities = DesiredCapabilities::chrome();
$capabilities->setCapability(ChromeOptions::CAPABILITY, $chromeOptions);

return RemoteWebDriver::create('http://localhost:4444/wd/hub', $capabilities);
```

* Go to a specified URL

```PHP
$driver->get('http://google.com');
$driver->navigate()->to('http://google.com');
```

> 'NOTE' -- the WebDriver may not wait for the page to load, you'd better using explicit and implicit waits.
