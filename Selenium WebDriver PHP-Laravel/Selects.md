# Selects workthough

* select com parte do texto

        $select = new Select($this->driver->findElement(
            By::id('IdUFConselhoProfissionalSolicitante')
        ));
        $options = $select->getOptions();

        foreach ($options as $elemento) {
            $texto = $elemento->getText();
            if (strstr($texto, $estado)) {
                $select->selectByVisibleText($texto);
                break;
            }
        }
