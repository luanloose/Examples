# Inputs workthough

* input with search dropdown

        $this->driver->findElement(By::id('busca-codigo-cbo'))
            ->sendKeys($cbo);

        $element = $this->driver->findElement(
            By::id(
                'ui-id-1'
            )
        );

        $this->driver->wait(10, 1000)->until(
            Condition::visibilityOf($element)
        );

        $this->driver->findElement(
            By::cssSelector(
                'a.ui-corner-all'
            )
        )->click();

* Input para mudar o valor via script

        $this->driver->executeScript("document.querySelector("."\"input[name='NAME']\").value = '". $value ."' ;");
