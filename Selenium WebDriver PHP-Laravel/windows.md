# Window workthough

## Executing somenthing in your code

```PHP
        // pegando a aba atual
        $abaAntes = $this->driver->getWindowHandles();

        //faz algo que abra a nova janela

        // acha a nova aba
        $abaDepois = $this->driver->getWindowHandles();
        $novaAba = array_diff($abaDepois, $abaAntes);

        // mudando de aba
        $this->driver->switchTo()->window(reset($novaAba));

        //faz o que tem que fazer

        //Volta para a aba anterior
        $this->driver->switchTo()->window(reset($abaAntes));
```
