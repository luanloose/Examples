# Buttons workthough

* When you have only part of a button text

        $elements = $this->driver->findElements(By::cssSelector('SELECTOR'));

        foreach ($elements as $element) {

            $botao = $element->GetAttribute("innerText");

            if ($botao === "TEXT") {
                $element->click();
                break;
            }
        }
