# Testes da aplicação exemplo

## Rodar testes

```CMD
./vendor/bin/phpunit
```

## Controler Subtração

```PHP
<?php
namespace App;
use App\Http\Controllers\Controller;

class Subtracao extends Controller
{
    private $num1;
    private $num2;

    /**
    * @return mixed
    */
    public function getNum1()
    {
        return $this->num1;
    }

    /**
    * @param mixed $num1
    */
    public function setNum1($num1 = null)
    {
        if(is_null($num1)) {
            throw new \InvalidArgumentException("Parametro nao informado");
        }

        $this->num1 = $num1;
    }

    /**
    * @return mixed
    */
    public function getNum2()
    {
        return $this->num2;
    }

    /**
    * @param mixed $num2
    */
    public function setNum2($num2 = null)
    {
        if(is_null($num2)) {
            throw new \InvalidArgumentException("Parametro nao informado");
        }

        $this->num2 = $num2;
    }

    public function subtrair()
    {
        return $this->num1 - $this->num2;
    }
}
```

## Testando o controler subtração

```PHP
<?php
namespace Tests;

use PHPUnit\Framework\TestCase;
use App\Http\Controllers\Subtracao;

class SubtracaoTest extends TestCase
{
    public function assertPreConditions()
    {
        $this->assertTrue(
            class_exists('App\Http\Controllers\Subtracao')
        );
    }

    public function testSubtracaoDeDoisNumeros()
    {
        $sub = new Subtracao();
        $sub->setNum1(15);
        $sub->setNum2(10);

        $this->assertEquals(5, $sub->subtrair());

        $sub = new Subtracao();
        $sub->setNum1(40);
        $sub->setNum2(30);

        $this->assertEquals(10, $sub->subtrair());
    }

    /**
    * @expectedException \InvalidArgumentException
    * @expectedExceptionMessage Parametro nao informado
    */
    public function testValidaSeValoresNaoForemPassados()
    {
        $sub = new Subtracao();
        $sub->setNum1(40);
        $sub->setNum2();
    }
}
```
