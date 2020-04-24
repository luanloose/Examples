# Webdriver PHP API workthough

* Open a browser

		// start an instance of firefox with selenium-webdriver
		
		$browser_type = 'firefox'
		$host = 'http://localhost:4444/wd/hub'

		$capabilities = array(\WebDriverCapabilityType::BROWSER_NAME => $browser_type);
		$driver = RemoteWebDriver::create($host, $capabilities);
		
		$browser_type
		# :firefox => firefox
		# :chrome  => chrome
		# :ie      => iexplore

*	Go to a specified URL

		$driver->get('http://google.com');
		$driver->navigate()->to('http://google.com');
		
	'NOTE' -- the WebDriver may not wait for the page to load, you'd better using explicit and implicit waits.

*	Locating Elements

	*	'findElement(WebDriverBy $by)' -- Find the first element matching the given arguments.
	
	*	'findElements(WebDriverBy $by)' -- Find all elements matching the given arguments

	*   'WebDriverBy' -- Class with static methods for selecting elements using different mechanisms.

	    *   'WebDriverBy
	        *  'class name'
            *  'css selector'
            *  'id'
            *  'name'
            *  'link text'
            *  'partial link text'
            *  'tag name'
            *  'xpath'

	*	Finding Element By ID

			# example html
			# <input id="q">...</input>
				
			$element = $driver->findElement(WebDriverBy::id("q"));
		
	*	By Class Name
	
			# example html
			# <div class="highlight-java" style="display: none; ">...</div>

			$element = $driver->findElement(WebDriverBy::className('highlight-java'));
		
	*	By Tag Name
			
			# example html
			# <div class="highlight-java" style="display: none; ">...</div>
			
			$element = $driver->findElement(WebDriverBy::tagName("div"));
			
	*	By Name
			
			# example html
			# <input id="q" name='search' type='text'>…</input>
			
		    $element = $driver->findElement(WebDriverBy::name('search'));

	*	By Link Text
			
			# example html
			# <a href="http://www.google.com/search?q=cheese">cheese</a>
			
			$element = $driver->findElement(WebDriverBy::linkText("cheese"));

	*	By Partial Link Text
	
			# example html
			# <a href="http://www.google.com/search?q=cheese">search for cheese</a>

			$element = $driver->findElement(WebDriverBy::partialLinkText("chee"));

	*	By XPath
	
			# example html
			# <ul class="dropdown-menu">
            #   <li><a href="/login/form">Login</a></li>
            #   <li><a href="/logout">Logout</a></li>
            # </ul>
  			
			$element = $driver->findElement(WebDriverBy::xpath('//a[@href='/logout']'));
			
	    *	`NOTE` -- When using Element#findElement with `WebDriverBy::xpath`, be aware that,
	
			*	 webdriver follows standard conventions: a search prefixed with "//" will search the entire document, not just the children of this current node. 
			*	Use ".//" to limit your search to the children of the receiving Element.
			
	* By CSS Selector
	
			# example html
			# <div id="food">
			#   <span class="dairy">milk</span>
			#   <span class="dairy aged">cheese</span>
			# </div>

			$element = $driver->findElement(WebDriverBy::cssSelector('#food span.dairy'));

        *	`WebDriverBy::cssSelector` more examples:
	
			*	 E[foo]        an E element with a "foo" attribute.
			*	E[foo="bar"]  an E element whose "foo" attribute value is exactly equal to "bar"   
            * E[foo="bar"]  an E element whose "foo" attribute value is exactly equal to "bar" (CSS 2)
            * E[foo~="bar"] an E element whose "foo" attribute value is a list of whitespace-separated values, one of which is exactly                  equal to "bar" (CSS 2)
            * E[foo^="bar"] an E element whose "foo" attribute value begins exactly with the string "bar" (CSS 3)
            * E[foo$="bar"] an E element whose "foo" attribute value ends exactly with the string "bar" (CSS 3)
            * E[foo*="bar"] an E element whose "foo" attribute value contains the substring "bar" (CSS 3)
            * E[foo|="en"]  an E element whose "foo" attribute has a hyphen-separated list of values beginning (from the left) with "en"            (CSS 2)

*	Element's operation

	*	Button/Link/Image

			$element = $driver->findElement(WebDriverBy::id('BUTTON_ID'))->click();
	
	*	Text Field
	
			# input some text
			$driver->findElement(WebDriverBy::id('BUTTON_ID'))->click();
			$driver->getKeyboard()->sendKeys('InputText');

			# send keyboard actions, press `cmd+a` & `delete`
            $driver->getKeyboard()
              ->sendKeys(array(
                WebDriverKeys::COMMAND, // Use control on non-mac computers.
                'a',
              ));

            $driver->getKeyboard()
              ->sendKeys(array(
                WebDriverKeys::BACKSPACE,
              ));

        *'Note' -- /RemoteWebElement->clear() will clear text from a textarea or a text input.

	*	Checkbox/Radio
	
			# check if it is selected
			$driver->findElement(WebDriverBy::id('CheckBox'))->isSelected();

			# select the element
			$driver->findElement(WebDriverBy::id('CheckBox'))->click();

			# deselect the element
			$driver->findElement(WebDriverBy::id('CheckBox'))->clears();
	
	*	Select
	
			# get the select element	
			$select = $driver->findElement(WebDriverBy::tagName('select'));

			# get all the options for this element
			$allOptions = $select->findElement(WebDriverBy::tagName('option'));

			# select the options
			foreach ($allOptions as $option) {
			  echo "Value is:" . $option->getAttribute('value);
			  $option->click();
			}

	*	visibility
			
			$driver->findElement(WebDriverBy::id('element'))->isDisplayed();
			
	*	get text
				
			$driver->findElement(WebDriverBy::id('element'))->getText();
	
	*	get attribute
			
			$driver->findElement(WebDriverBy::id('element'))->getAttribute('class');
			
*	Driver's operation

	* execute javascript

			$driver->executeScript("return window.location.pathname");

	* wait for a specific element to show up
			
			# set the timeout to 20 seconds, and the time in interval to 1000 ms

            $driver->wait(20, 1000)->until(
                WebDriverExpectedCondition::titleIs('WebDriver Page')
            );

	
	* implicit waits

	An implicit wait is to tell WebDriver to poll the DOM for a certain amount of time when trying to find an element or elements if they are not immediately available
	
			# set the timeout for implicit waits as 10 seconds
			$driver->manage()->timeouts()->implicitlyWait = 10
			
			$driver->get("http://somedomain/url_that_delays_loading");
			$element = $driver->findElement(WebDriverBy::id('some-dynamic-element'));

	* switch between frames
	
			# switch to an iframe
			$driver->switchTo()->frame(/WebDriverElement('the id or the name of the frame"some-frame" # name or id'));

			# switch back to the main document
			$driver->switchTo()->defaultContent();
				
	* swich between windows
	
			#TODO: Add examples.
			
	* handle javascript dialog
		
			# get the alert

			$a = $driver->switchTo->alert();

			# operation on the alert

			if ($a->getText == 'A value you are looking for') {
			  a->dismiss();
			}
			else {
			  a->accept();
			}

* Cookies
	
	* Delete cookies
	
			# You can delete cookies in 2 ways
			# By name
			$driver->manage()->deleteCookieNamed('CookieName');

			# Or all of them
			$driver->manage()->deleteAllCookies();
