# PHP
> Boas práticas no desenvolvimento

1. Visão Geral
--------------

- Script só deve usar `<?php`.
- Usar somente UTF-8 without BOM.
- Indentação de 4 espaços ou tab.


2. Namespaces e Classes
-----------------------

- Os nomes de classe devem ser declaradas em `StudlyCaps`.

```php
<?php
// PHP 5.3 and later:
namespace Vendor\Model;

class Foo
{
}
```

3. Classes, Constantes e Métodos
--------------------------------

### 3.1. Constantes

- Sempre em caixa alta

```php
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

### 3.2. Propriedades

- Não usar ```var```
- Sempre declarar visibilidade

```php
<?php
namespace Vendor\Package;

class ClassName
{
	// bad
	var $foo = null;
	var $foo=null;
	var $foo=NULL;
	var $foo_bar = null;
	var $FooBar = null;
	
	// good
    public $foo = null;
	public $fooBar = null;
}
```

### 3.3. Métodos

- Nome do método deve ser declarado em `camelCase()`.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

### 3.4. Palavra-chave e True/False/Null

- Palavras-chave do PHP deve estar em letra minúscula.

- `true`, `false`, and `null` deve estar em letra minúscula.

[Palavras-chave]: http://php.net/manual/en/reserved.keywords.php


4. Estrutura de controle
------------------------

As regras gerais são as seguintes:

- Deve haver um espaço após a palavra-chave estrutura de controle
- Não deve haver um espaço após o parêntese de abertura
- Não deve haver um espaço antes do parêntese de fechamento
- A chave de fechamento deve estar na linha seguinte depois que o corpo

### 4.1. `if`, `elseif`, `else`

```php
<?php

// bad
if($exp) $var=2;

// good
if ($exp) {
	$var = 2;
}
```

### 4.2. `foreach`

```php
<?php

// bad
foreach($iterable as $key=>$value){
	// code...
}

// bad
foreach($iterable as $key => $value)
{
	// code...
}

// good
foreach ($iterable as $key => $value) {
    // foreach body
}
```