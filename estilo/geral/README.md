# Geral
> diretrizes gerais para escrever código bonito

## Sumário

- [Idioma](#idioma)
- [Formatação](#formata%C3%A7%C3%A3o)
- [Ordenação](#ordena%C3%A7%C3%A3o)

[[⬅︎ Voltar para Estilo]](https://github.com/mktvirtual/guides/tree/master/estilo)

## Idioma

- Escreva código em inglês.
    - Todo código deve estar em inglês, incluindo documentação, comentários, nomes de variáveis e atributos de objetos.
    - Sinta-se livre para criar traduções se for realmente importante.

## Formatação

- Não cometa erros de ortografia.
    ```javascript
    // bad
    var messagi;

    // good
    var message;
    ```

- Evite comentários na mesma linha
    ```javascript
    var list = []; // bad

    // good
    var list = [];
    ```

- Quebre linhas com mais de 80 caracteres
    ```javascript
    // bad
    var message = 'this is a very long message that will probably hurt this style guide so I can explain how to properly use it';

    // good
    var message = 'this is a very long message that was broken'+
        ' to not hurt this style guide';
    ```

- Exclua espaços após o final da linha
    ```javascript
    // bad
    if (user.name === 'Bruno') {
        type = 'Samurai';∙∙∙
    } else {
        type = 'Human';∙
    }

    // good
    if (user.name === 'Bruno') {
        type = 'Samurai';
    } else {
        type = 'Human';
    }
    ```

- Use 4 espaços para indentação (não `tab`)
    ```javascript
    // bad
    for (var i = 0, len = obj.length; i < len; i++) {
    ∙∙console.log(obj[i]);
    }

    // good
    for (var i = 0, len = obj.length; i < len; i++) {
    ∙∙∙∙console.log(obj[i]);
    }
    ```

- Indente linhas contínuas com 4 espaços.
    ```javascript
    // bad
    var $users = $('.user'),
    ∙∙$posts = $('.post');

    // good
    var $users = $('.user'),
    ∙∙∙∙$posts = $('.post');
    ```

- Use linhas em branco em volta de blocos com múltiplas linhas
    ```scss
    // bad
    .user {
        border: 1px solid #000;
        color: #f00;
    }
    .post {
        border: 1px solid #f00;
        color: #000;
    }

    // good
    .user {
        border: 1px solid #000;
        color: #f00;
    }

    .post {
        border: 1px solid #f00;
        color: #000;
    }
    ```

- Use espaços em volta de operadores, depois de vírgulas, depois de dois-pontos e ponto-e-virgulas, em volta de `{` e antes de `}`.
    ```javascript
    // bad
    var i,total=10,obj=[];
    for (i=0;i<total;i++){
        obj[i]=i;
    }

    // good
    var i, total = 10, obj = [];
    for (i = 0; i < total; i++) {
        obj[i] = i;
    }
    ```

- Não use espaços depois de `(`, `[` ou antes de `]`, `)`.
    ```javascript
    var messages = [
        'please do not do that',
        'better this way'
    ];
    // bad
    console.log( messages[ 0 ] );

    // good
    console.log(messages[0]);
    ```

- Evite abreviações.
    ```javascript
    // bad
    var l = [],
        u = {};

    // good
    var list = [],
        users = {};
    ```

- Evite usar o tipo do objeto no nome da variável.
    ```javascript
    // bad
    var userObject = {};

    // good
    var user = {};
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Ordenação
- Ordene métodos para que os métodos que chamam estejam antes que os métodos que eles chamam no arquivo.
- Ordene métodos para que eles estejam o mais perto possível daqueles que eles chamam.

[[⬆︎ Topo]](#sum%C3%A1rio)
