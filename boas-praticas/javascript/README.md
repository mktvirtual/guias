# Javascript
> Boas práticas


## Sumário

- [Formatação](#formata%C3%A7%C3%A3o)
- [Escopo](#escopo)
- [Objeto literal](#objeto-literal)
- [Referências](#refer%C3%AAncias)

[[⬅︎ Voltar para Boas Práticas]](https://github.com/mktvirtual/guides/tree/master/boas-praticas)

## Variáveis

- Use `var` para declarar variáveis.
    - Quando você declara uma variável sem `var`, ela vaza para o escopo global.
    ```javascript
    // bad
    me = 'globalization';

    // good
    var me = 'better this way';
    ```

- Declare variáveis acima de sua chamada.
    - Isto impede o [*variable hoisting*](http://code.tutsplus.com/tutorials/javascript-hoisting-explained--net-15092)
    ```javascript
    // bad
    var john = person; // => null

    // bad
    var john = person; // => undefined
    var person = { age: 23 };

    // good
    var person = { age: 23 };
    var john = person; // => { age: 23 }
    ```

- Evite variáveis globais.
    - Ao atingirem o escopo global, as variáveis podem ser acessadas por qualquer um. Além disso, uma variável pode tomar o valor de outra se tiverem o mesmo nome. Evite ao máximo expor variáveis globalmente.

- Use *Immediately-Invoked Function Expression* para expor somente as variáveis necessárias ao escopo global. [(?)](http://gregfranko.com/blog/i-love-my-iife/)
    ```javascript
    (function(){
        var Person = {
            // ...
        }
        
        var PublicPerson = {
            // ...
        }
        window.PublicPerson = PublicPerson;

        console.log(Person); // => Person
        console.log(PublicPerson); // => PublicPerson
    }());

    console.log(Person); // => ReferenceError: Person is not defined
    console.log(PublicPerson); // => PublicPerson
    ```

- Prefira objetos a muitos parâmetros.
    ```javascript
    // bad
    var setUserInfo = function(user, firstName, lastName, birthDay, gender) {
        user.firstName = firstName;
        user.lastName = lastName;
        
        // ...
    };

    // good
    var setUserInfo = function(user, info){
        user.firstName = info.firstName;
        user.lastName = info.lastName;
        
        // ...
    };
    ```

## Condicionais

- Prefira `===` e `!==` em comparações estritas. [(?)](http://stackoverflow.com/questions/359494/does-it-matter-which-equals-operator-vs-i-use-in-javascript-comparisons)
    ```javascript
    // bad
    5 == '5'; // => true
    5 == 6; // => false
    5 == 5; // => true

    0 == false; // => true
    0 == ''; // => true
    0 == 0; // => true
    0 == 1; // => false

    // good
    5 === '5'; // => false
    5 === 6; // => false
    5 === 5; // => true

    0 === false; // => false
    0 === ''; // => false
    0 === 0; // => true
    ```

## jQuery

- Faça cache de objetos jQuery.
    ```javascript
    // bad
    function setSidebar() {
        $('.sidebar').hide();

        // ...stuff...

        $('.sidebar').css({
            'background-color': 'pink'
        });
    }

    // good
    function setSidebar() {
        var $sidebar = $('.sidebar');
        $sidebar.hide();

        // ...stuff...

        $sidebar.css({
            'background-color': 'pink'
        });
    }
    ```

- Prefira DOM queries. Use `find` em objetos jQuery já existentes. [Teste no jsPerf](http://jsperf.com/jquery-find-vs-context-sel/16).
    ```javascript
    // bad
    $('ul', '.sidebar').hide();

    // bad
    $('.sidebar').find('ul').hide();

    // good
    $('.sidebar ul').hide();

    // good
    $('.sidebar > ul').hide();

    // good
    $sidebar.find('ul').hide();
    ```

## Objetos

- Use a sintaxe literal para declarar objetos
    ```javascript
    // bad
    var item = new Object();

    // good
    var item = {};
    ```

- Não use [palavras reservadas](http://es5.github.io/#x7.6.1) como chaves. Não funciona no IE8.
    ```javascript
    // bad
    var superman = {
        default: {
            clark: 'kent'
        },
        private: true
    };

    // good
    var superman = {
        defaults: {
            clark: 'kent'
        },
        hidden: true
    };
    ```

- Use sinônimos para palavras reservadas.
    ```javascript
    // bad
    var superman = {
        class: 'alien'
    };

    // bad
    var superman = {
        klass: 'alien'
    };

    // good
    var superman = {
        type: 'alien'
    };
    ```

- Use *dot notation* (`user.name`) para acessar valores de propriedades com o nome conhecido.
    ```javascript
    var user = { name: 'john' };

    // bad
    console.log(user["name"]);

    // good
    console.log(user.name);
    ```

- Use *bracket notation* (`user["name"]`) para acessar propriedades com o nome armazenado em uma variável.
    ```javascript
    var user = {
        name: 'john',
        age: 21
    };

    // good
    for (var key in user) {
        console.log(user[key]);
    }
    ```

## Referências

- [Learning JavaScript Design Patterns](http://addyosmani.com/resources/essentialjsdesignpatterns/book/)

- [Book: Build Better Apllications with Coding and Design Patterns | JavaScript Patterns Stoyan Stefanov, O'Reilly](http://shop.oreilly.com/product/9780596806767.do)
