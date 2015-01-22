# JavaScript
> guia anti-espaguete

## Sumário
- [Formatação](#formata%C3%A7%C3%A3o)
- [Nomenclatura](#nomenclatura)
- [Manipulação do DOM](#manipula%C3%A7%C3%A3o-do-dom)
- [Referências](#refer%C3%AAncias)

[[⬅︎ Voltar para Estilo]](https://github.com/mktvirtual/guias/tree/master/estilo)


## Formatação

- Use ponto-e-vírgula.
    ```javascript
    // ruim
    var me = $(this)
    test()

    // bom
    var me = $(this);
    test();
    ```

- Use aspas simples.
    ```javascript
    // ruim
    var string = "<p class='foo'>Lorem Ipsum</p>";
    var noteClick = me.attr("data-note");

    // bom
    var string = '<p class="foo">Lorem Ipsum</p>';
    var noteClick = me.attr('data-note');
    ```

- Use `{}` em todos os blocos.
    ```javascript
    // ruim
    if (condition) statement;
    else if (condition) statement;
    else statement;

    // bom
    if (condition) {
        statement
    } else if (condition) {
        statement
    } else {
        statement
    }
    ```

- Use `/* comentários */`.
    - Inclua uma descrição, especifique tipos e valores para todos os parâmetros e retornos de funções e métodos.
    ```javascript
    /**
     * make() returns a new element
     * based on the passed in tag name
     *
     * @param <String> tag
     * @return <Element> element
     */
    function make(tag) {

        // stuff...

        return element;
    }
    ```

- Use `// comentários`.
    - Explique o que está acontecendo no seu código.
    ```javascript
    // bom
    function getType() {
        console.log('fetching type...');

        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }
    ```

- Prefixe objetos jQuery com `$`.
    ```javascript
    // ruim
    var sidebar = $('.sidebar');

    // bom
    var $sidebar = $('.sidebar');
    ```

- Use variáveis em `lowerCamelCase`
    ```javascript
    // ruim
    var main_title, maintitle;

    // bom
    var mainTitle;
    ```

- Use `{` na mesma linha da sentença.
    ```javascript
    // ruim
    // the function returns undefined and not an object with a name property
    function func()
    {
        return
        {
            name: "Batman"
        };
    }
    // => undefined

    // bom
    function func() {
        return {
            name: "Batman"
        };
    }
    // => { name: "Batman" }
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Nomenclatura

- Use `camelCase` para variáveis normais.
    ```javascript
    // ruim
    var table_prefix = 'table-';
    var tableprefix = 'table-';
    var TablePrefix = 'table-';

    // bom
    var tablePrefix = 'table-';
    ```

- Use `PascalCase` para "classes".
    ```javascript
    // ruim
    var app = { /* ... */ };

    // bom
    var App = { /* ... */ };
    ```

- Use `UPPER_CASE` para constantes.
    ```javascript
    // ruim
    var maxWidth = 300;

    // bom
    var MAX_WIDTH = 300;
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Manipulação do DOM

- Use o prefixo `js-` nas classes de elementos selecionados pelo JavaScript. [(?)](https://github.com/csswizardry/CSS-Guidelines#js-hooks)
    ```javascript
    // ruim
    var $button = $('.button');

    // bom
    var $button = $('.js-button');
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Referências

- [Coding Style por @LFeh](https://github.com/LFeh/coding-style#js)
    - Grande parte dos exemplos daqui vieram deste ótimo guia por [@LFeh](https://github.com/LFeh).

[[⬆︎ Topo]](#sum%C3%A1rio)
