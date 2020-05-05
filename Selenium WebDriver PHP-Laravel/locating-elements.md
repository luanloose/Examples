# Webdriver PHP API workthough

## Locating Elements

* 'findElement(WebDriverBy $by)' -- Find the first element matching the given arguments.

* 'findElements(WebDriverBy $by)' -- Find all elements matching the given arguments

* 'WebDriverBy' -- Class with static methods for selecting elements using different mechanisms.

  * 'class name'
  * 'css selector'
  * 'id'
  * 'name'
  * 'link text'
  * 'partial link text'
  * 'tag name'
  * 'xpath'

* Finding Element By ID

```PHP
// example html
// <input id="q">...</input>

$element = $driver->findElement(WebDriverBy::id("q"));
```

* By Class Name

```PHP
// example html
// <div class="highlight-java" style="display: none; ">...</div>

$element = $driver->findElement(WebDriverBy::className('highlight-java'));
```

* By Tag Name

```PHP
// example html
// <div class="highlight-java" style="display: none; ">...</div>

$element = $driver->findElement(WebDriverBy::tagName("div"));
```

* By Name

```PHP
// example html
// <input id="q" name='search' type='text'>…</input>

$element = $driver->findElement(WebDriverBy::name('search'));
```

* By Link Text

```PHP
// example html
// <a href="http://www.google.com/search?q=cheese">cheese</a>

$element = $driver->findElement(WebDriverBy::linkText("cheese"));
```

* By Partial Link Text

```PHP
// example html
// <a href="http://www.google.com/search?q=cheese">search for cheese</a>

$element = $driver->findElement(WebDriverBy::partialLinkText("chee"));
```

* By XPath

```PHP
// example html
// <ul class="dropdown-menu">
// <li><a href="/login/form">Login</a></li>
// <li><a href="/logout">Logout</a></li>
// </ul>

$element = $driver->findElement(WebDriverBy::xpath('//a[@href='/logout']'));
```

> `NOTE` -- When using `WebDriverBy::xpath` be aware that,
>
> Webdriver follows standard conventions: a search prefixed with "//" will search the entire document, not just the children of this current node.
>
> Use ".//" to limit your search to the children of the receiving Element.

* By CSS Selector

```PHP
// example html
// <div id="food">
//  <span class="dairy">milk</span>
//  <span class="dairy aged">cheese</span>
// </div>

$element = $driver->findElement(WebDriverBy::cssSelector('#food span.dairy'));
```

* `WebDriverBy::cssSelector` more examples:

  * E[foo] an E element with a "foo" attribute.
  * E[foo="bar"] an E element whose "foo" attribute value is exactly equal to "bar"
  * E[foo="bar"]  an E element whose "foo" attribute value is exactly equal to "bar" (CSS 2)
  * E[foo~="bar"] an E element whose "foo" attribute value is a list of whitespace-separated values, one of which is  exactly equal to "bar" (CSS 2)
  * E[foo^="bar"] an E element whose "foo" attribute value begins exactly with the string "bar" (CSS 3)
  * E[foo$="bar"] an E element whose "foo" attribute value ends exactly with the string "bar" (CSS 3)
  * E[foo*="bar"] an E element whose "foo" attribute value contains the substring "bar" (CSS 3)
  * E[foo|="en"]  an E element whose "foo" attribute has a hyphen-separated list of values beginning (from the left) with "en" (CSS 2)

* visibility

```PHP
$driver->findElement(WebDriverBy::id('element'))->isDisplayed();
```

* get text

```PHP
$driver->findElement(WebDriverBy::id('element'))->getText();
```

* get attribute

```PHP
$driver->findElement(WebDriverBy::id('element'))->getAttribute('class');
```
