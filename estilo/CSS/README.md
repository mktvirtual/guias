# CSS
> códigos de estilo estilosos

## Sumário
- [Formatação](#formata%C3%A7%C3%A3o)
- [Seletores](#seletores)
- [Ordenação](#ordena%C3%A7%C3%A3o)
- [Organização](#organiza%C3%A7%C3%A3o)
- [Referências](#refer%C3%AAncias)

[[⬅︎ Voltar para Estilo]](https://github.com/mktvirtual/guides/tree/master/estilo)

## Formatação
- Use [Sass](http://sass-lang.com/).
    - Sass nos dá poder para escrever CSS modular, com variáveis, condicionais, funções e mais. Use-o.

- Prefira a sintaxe `Scss`.
    - Você escreve mais no `Scss`, ele utiliza símbolos e `@include` em vez de `+`, mas utilizando-o seu código será muito mais legível e mais fácil de compreender. Ele também é a única variação do Sass que é compatível com o [libsass](https://github.com/hcatlin/libsass), um compilador muito rápido escrito em C.

- Use hifens quando nomear mixins, extends, classes, funções e variáveis.
    ```scss
    // bad
    $colorUser = #f00;
    $color_user = #f00;

    // good
    $color-user = #f00;
    ```

- Use uma declaração por linha.
    ```scss
    // bad
    .nav, .nav--inline, .nav--stacked {
        // ...
    }

    // good
    .nav,
    .nav--inline,
    .nav--stacked {
        // ...
    }
    ```

- Use espaço entre uma propriedade e seu valor.
    ```scss
    .post {
        // bad
        color:#f00;

        // good
        background-color: #00f;
    }
    ```

- Use aspas duplas.
    ```scss
    // bad
    .nav:after,
    [type='text'],
    [class^='...'] {
        content: '';
    }

    // good
    .nav:after,
    [type="text"],
    [class^="..."] {
        content: "";
    }
    ```

- Prefira cores em hexadecimal, quando possível.
    ```scss
    // bad
    color: white;
    color: rgb(0, 0, 0);

    // good
    color: #fff;
    color: rgba(0, 0, 0, 0.7);
    ```

- Use variáveis para cores, com o prefixo `color-`.
    ```scss
    // bad
    color: #c7f464;

    // good
    $color-lime: #c7f464;
    color: $color-lime;
    ```

- Use nomes de variáveis com significado semântico.
    ```scss
    // bad
    $color-red: #f00;
    color: $color-red;

    // good
    $color-red: #f00;
    $color-text: $color-red;
    color: $color-text;
    ```

- Use letras em minúsculo, incluindo cores.
    ```scss
    // bad
    color: #FFF;

    // good
    color: #fff;
    ```

- Não especifique a unidade após valores 0, a não ser que sejam necessárias em um mixin.
    ```scss
    // bad
    margin: 0px;

    // good
    margin: 0;
    ```

- `Scss` Use ponto-e-virgula no final das linhas.
    ```scss
    // bad
    .post {
        color: $color-post-text
    }

    // good
    .post {
        color: $color-post-text;
    }
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Seletores

- Não coma vogais.
    ```scss
    // bad
    .npt {
        border: 1px solid $color-border;
    }

    // good
    .input {
        border: 1px solid $color-border;
    }
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Ordenação
- Coloque `@extend` e `@include` no topo da sua lista de declarações.
    ```scss
    // bad
    .post {
        color: #f00;
        font-weight: 300;
        @extend %island;
    }

    // good
    .post {
        @extend %island;
        color: #f00;
        font-weight: 300;
    }
    ```

- Coloque seletores concatenados em segundo.
    - `.post.featured`

- Coloque pseudo seletores em terceiro.
    - `.post:hover`

- Coloque seletores aninhados por último.
    - `.post .title`

- Use ordenação por relevância para propriedades, não alfabética.
    - Para elementos `box`, propriedades de dimensionamento são mais importantes do que aquelas que estilizam o texto. Em elementos `inline` é o oposto. Ao ordenar por relevância, você facilita a leitura das propriedades.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Organização

- Crie arquivos para cada componente.
    - Isso facilita a organização dos seus estilos.

- Prefira `@import`ar todos os seus componentes em um só arquivo `main.css`.
    - Importar em um só arquivo traz o grande benefício de utilizar qualquer componente em qualquer tela.
    ```scss
    @import "component";
    @import "component";
    ```

- Utilize um bom esquema para nomenclatura.
    - Um bom esquema para nomear suas classes é essencial. O preferido é o [BEM](https://github.com/csswizardry/CSS-Guidelines#naming-conventions), que é bem explícito e de fácil entendimento.

- Divida blocos de código com comentários.
    ```scss
    /*------------------------------------*\
        #POST
    \*------------------------------------*/

    .post {
        margin: 10px 0;
        // ...
    }
    ```

- Evite código específico para páginas.
    - Se você dividir bem seus componentes, você poderá utilizá-los em outras páginas se necessário.
    - Antes de escrever um código específico para uma página, se pergunte se isto não é apenas uma variação de algum componente. Se for, introduza a variação ao componente.
    - Sempre converse com o designer, desde o início do projeto, sobre padronizar componentes.

- Evite ter arquivos com mais de 150 linhas.
    - Mais do que isso e você provavelmente está fazendo errado. Abstraia componentes. Sempre.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Referências
- [CSS Guidelines](https://github.com/csswizardry/CSS-Guidelines)
    - Utilize estas diretrizes para escrever CSS da melhor forma. Grande parte deste guia foi baseado nele.
- [Guides por Thoughtbot](https://github.com/thoughtbot/guides/tree/master/style)
    - Este guia também é uma adaptação do Guides da Thoughtbot.

[[⬆︎ Topo]](#sum%C3%A1rio)
