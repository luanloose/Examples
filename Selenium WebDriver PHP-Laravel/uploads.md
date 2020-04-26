# Upload workthough

* Image

```PHP
        $fileInput = $this->driver->findElement(By::id('fupDoc'));
        $fileInput->setFileDetector(new LocalFile());

        //decode base64 string
        $imagem = base64_decode($imagem);

        $safeName = 'teste.' . 'jpg';
        Storage::disk('public')->put($safeName, $imagem);

        // upload
        $fileInput->sendKeys($this->path . $safeName);
        $this->driver->findElement(
            By::id('btnAdicionar')
        )->click();

        Storage::delete($this->path . $safeName);
```