# JavaScript
> guia anti-espaguete

## Sumário
- [Formatação](#formata%C3%A7%C3%A3o)
- [Referências](#refer%C3%AAncias)

[[⬅︎ Voltar para Estilo]](https://github.com/mktvirtual/guides/tree/master/estilo)


## Formatação

- Use ponto-e-vírgula
    ```javascript
    // bad
    var me = $(this)
    test()

    // good
    var me = $(this);
    test();
    ```

- Use aspas simples
    ```javascript
    // bad
    var string = "<p class='foo'>Lorem Ipsum</p>";
    var noteClick = me.attr("data-note");

    // good
    var string = '<p class="foo">Lorem Ipsum</p>';
    var noteClick = me.attr('data-note');
    ```

- Use `{}` em todos os blocos
    ```javascript
    // bad
    if (condition) statement;
    else if (condition) statement;
    else statement;

    // good
    if (condition) {
        statement
    } else if (condition) {
        statement
    } else {
        statement
    }
    ```

- Use `/** ... */` para comentários em múltiplas linhas. Inclua uma descrição, especifique tipos e valores para todos os parâmetros e retornos.
    ```javascript
    // bad
    // make() returns a new element
    // based on the passed in tag name
    //
    // @param <String> tag
    // @return <Element> element
    function make(tag) {

        // ...stuff...

        return element;
    }

    // good
    /**
     * make() returns a new element
     * based on the passed in tag name
     *
     * @param <String> tag
     * @return <Element> element
     */
    function make(tag) {

        // ...stuff...

        return element;
    }
    ```

- Use `//` para comentários em uma única linha, acima do seu contexto. Adicione uma linha em branco acima do comentário.
    ```javascript
    // bad
    var active = true;  // is current tab

    // good
    // is current tab
    var active = true;

    // bad
    function getType() {
        console.log('fetching type...');
        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }

    // good
    function getType() {
        console.log('fetching type...');

        // set the default type to 'no type'
        var type = this._type || 'no type';

        return type;
    }
    ```

- Não utilize vírgulas na frente da linha.
    ```javascript
    // bad
    var once
        , upon
        , aTime;

    // good
    var once,
        upon,
        aTime;

    // bad
    var hero = {
          firstName: 'Bob'
        , lastName: 'Parr'
        , heroName: 'Mr. Incredible'
        , superPower: 'strength'
    };

    // good
    var hero = {
        firstName: 'Bob',
        lastName: 'Parr',
        heroName: 'Mr. Incredible',
        superPower: 'strength'
    };
    ```

- Prefixe objetos jQuery com `$`
    ```javascript
    // bad
    var sidebar = $('.sidebar');

    // good
    var $sidebar = $('.sidebar');
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Referências

- [Coding Style por @LFeh](https://github.com/LFeh/coding-style#js)
    - Grande parte dos exemplos daqui vieram deste ótimo guia por [@LFeh](https://github.com/LFeh)

[[⬆︎ Topo]](#sum%C3%A1rio)
