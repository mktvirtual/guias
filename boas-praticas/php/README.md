# PHP
> Boas práticas no desenvolvimento

1. Visão Geral
--------------

- Files MUST use only `<?php` and `<?=` tags.

- Files MUST use only UTF-8 without BOM for PHP code.

- Code MUST follow a "coding style guide" PSR [[PSR-1]].

- Code MUST use 4 spaces for indenting, not tabs.

- Namespaces and classes MUST follow an "autoloading" PSR: [[PSR-0], [PSR-4]].

- Class names MUST be declared in `StudlyCaps`.

- Class constants MUST be declared in all upper case with underscore separators.

- Method names MUST be declared in `camelCase`.


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

### 3.4. Keywords and True/False/Null

PHP [keywords] MUST be in lower case.

The PHP constants `true`, `false`, and `null` MUST be in lower case.

[keywords]: http://php.net/manual/en/reserved.keywords.php


4. Control Structures
---------------------

The general style rules for control structures are as follows:

- There MUST be one space after the control structure keyword
- There MUST NOT be a space after the opening parenthesis
- There MUST NOT be a space before the closing parenthesis
- There MUST be one space between the closing parenthesis and the opening
  brace
- The structure body MUST be indented once
- The closing brace MUST be on the next line after the body

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