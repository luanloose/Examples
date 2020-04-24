# Repeat tasks workthough

* Do more than once

        foreach ($elements as $element) {

            $this->driver->findElement(By::id('AutoCompleteProcedimento'))
                ->sendKeys($element['Key1']);

            $this->driver->findElement(By::cssSelector('SELECTOR'))->click();

            $this->driver->findElement(By::id('ID'))
                ->sendKeys($element['Key2']);

            $this->driver->findElement(
                By::id('ID')
            )->click();

            sleep(2);
        }
