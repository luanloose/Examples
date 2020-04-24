# Tables workthough

* Capturing N Elements

        $line = $this->driver->findElements(
            By::cssSelector('td.content')
        );

        $cont = (count($line) - 1) / 7;

        $l = 0; //number to find elements
        $this->result = [];

        for ($i = 1; $i <= $cont; $i++) {

            array_push($this->result, [
                "Key 1" => $line[1 + $l]->getText(),
                "Key 2" => $line[2 + $l]->getText(),
                "Key 3" => $line[3 + $l]->getText(),
                "Key 4" => $line[4 + $l]->getText()
            ]);

            $l += 7; //number of colunms
        }
