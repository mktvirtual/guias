# Geral
> diretrizes gerais para escrever código bonito

## Sumário

- [Idioma](#idioma)
- [Formatação](#formata%C3%A7%C3%A3o)
- [Ordenação](#ordena%C3%A7%C3%A3o)

[[⬅︎ Voltar para Estilo]](https://github.com/mktvirtual/guides/tree/master/estilo)

## Idioma

- Escreva código em inglês.
    - Todo código deve estar em inglês, incluindo nomes de variáveis e atributos de objetos.
    - Sinta-se livre para criar traduções se for realmente importante.

- Escreva comentários, documentação em português
    - Para facilitar a leitura para toda a equipe, conteúdo de suporte ao código (documentação, comentários, commits) devem ser escritos em português
    - Se este conteúdo já estiver em inglês, continue escrevendo em inglês.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Formatação

- Não cometa erros de ortografia.
    ```javascript
    // ruim
    var messagi;

    // bom
    var message;
    ```

- Evite linhas com mais de 80 caracteres.
    - As vezes é inevitável, mas quase sempre podemos ser mais explícitos e coesos ao dividir o código em mais linhas.

    ```javascript
    // ruim
    var message = 'this is a very long message that will probably hurt this style guide so I can explain how to properly use it';

    // bom
    var message = 'this is a very long message that was broken'+
        ' to not hurt this style guide';
    ```

- Use 4 espaços para indentação (não `tab`).
    ```javascript
    // ruim
    for (var i = 0, len = obj.length; i < len; i++) {
    ∙∙console.log(obj[i]);
    }

    // bom
    for (var i = 0, len = obj.length; i < len; i++) {
    ∙∙∙∙console.log(obj[i]);
    }
    ```

- Use linhas em branco em volta de blocos com múltiplas linhas.
    ```scss
    // ruim
    .user {
        border: 1px solid #000;
        color: #f00;
    }
    .post {
        border: 1px solid #f00;
        color: #000;
    }

    // bom
    .user {
        border: 1px solid #000;
        color: #f00;
    }

    .post {
        border: 1px solid #f00;
        color: #000;
    }
    ```

- Use espaços.
    - Eles são grandes amigos para melhorar a legibilidade do seu código.

    ```javascript
    // ruim
    var i,total=10,obj=[];
    for (i=0;i<total;i++){
        obj[i]=i;
    }

    // bom
    var i, total = 10, obj = [];
    for (i = 0; i < total; i++) {
        obj[i] = i;
    }
    ```

- Não use espaços depois de `(`, `[` ou antes de `]`, `)`.
    ```javascript
    // ruim
    console.log( messages[ 0 ] );

    // bom
    console.log(messages[0]);
    ```

- Evite abreviações. Prefira variáveis com nomes explicativos, mesmo que fiquem grandes
    ```javascript
    // ruim
    var l = [],
        u = {},
        bul = [];

    // bom
    var list = [],
        users = {},
        blockedUsersList = [];
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Ordenação
- Ordene métodos para que os métodos que chamam estejam antes que os métodos que eles chamam no arquivo.
- Ordene métodos para que eles estejam o mais perto possível daqueles que eles chamam.
- Ordene declarações e blocos para que estejam perto de outras declarações e blocos dentro do mesmo contexto.
- Não use ordenação alfabética.

[[⬆︎ Topo]](#sum%C3%A1rio)
