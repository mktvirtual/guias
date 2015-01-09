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

- Use a sintaxe `Scss`.
    - Você escreve mais no `Scss`, ele utiliza símbolos e `@include` em vez de `+`, mas utilizando-o seu código será muito mais legível e mais fácil de compreender. Ele também é a única variação do Sass que é compatível com o [libsass](https://github.com/hcatlin/libsass), um compilador muito rápido escrito em C utilizado por nossas ferramentas de automação.

- Use hifens quando nomear mixins, extends, classes, funções e variáveis.
    ```scss
    // ruim
    $colorUser = #f00;
    $color_user = #f00;

    // bom
    $color-user = #f00;
    ```

- Use uma declaração por linha.
    ```scss
    // ruim
    .nav, .nav--inline, .nav--stacked {
        // ...
    }

    // bom
    .nav,
    .nav--inline,
    .nav--stacked {
        // ...
    }
    ```

- Use espaço entre uma propriedade e seu valor.
    ```scss
    .post {
        // ruim
        color:#f00;

        // bom
        background-color: #00f;
    }
    ```

- Use aspas duplas.
    ```scss
    // ruim
    .nav:after,
    [type='text'],
    [class^='...'] {
        content: '';
    }

    // bom
    .nav:after,
    [type="text"],
    [class^="..."] {
        content: "";
    }
    ```

- Use variáveis para cores, com o prefixo `color-`.
    ```scss
    // ruim
    color: #c7f464;

    // bom
    $color-lime: #c7f464;
    color: $color-lime;
    ```

- Use nomes de variáveis com significado semântico.
    - Ao usar nomes semânticos podemos reutilizar variáveis com facilidade, além deixar muito claro para os desenvolvedores qual a função de cada cor

    ```scss
    // ruim
    $color-red: #f00;
    color: $color-red;

    // bom
    $color-red: #f00;
    $color-text: $color-red;
    color: $color-text;
    ```

- `Scss` Use ponto-e-virgula no final das linhas.
    ```scss
    // ruim
    .post {
        color: $color-post-text
    }

    // bom
    .post {
        color: $color-post-text;
    }
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Seletores

- Não coma vogais.
    ```scss
    // ruim
    .npt {
        border: 1px solid $color-border;
    }

    // bom
    .input {
        border: 1px solid $color-border;
    }
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Ordenação
- Coloque `@extend` no topo da sua lista de declarações.
    ```scss
    // ruim
    .post {
        color: #f00;
        font-weight: 300;
        @extend %island;
    }

    // bom
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
    - Para elementos `box`, propriedades de dimensionamento são mais importantes do que aquelas que estilizam o texto. Em elementos `inline` é o oposto. Ao ordenar por relevância, você facilita a leitura das propriedades. Você também pode dividir contextos (declarações de tamanho, de cor, de animação) com uma linha em branco.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Organização

- Crie arquivos para cada componente.
    - Isso facilita a organização dos seus estilos.

- Prefira `@import`ar todos os seus componentes em um só arquivo `main.css`.
    - Importar em um só arquivo traz o grande benefício de utilizar qualquer componente em qualquer tela.

    ```scss
    @import "component1";
    @import "component1";
    ```

- Utilize um bom esquema para nomenclatura.
    - Um bom esquema para nomear suas classes é essencial. O preferido é o [BEM](https://github.com/csswizardry/CSS-Guidelines#naming-conventions), que é bem explícito e de fácil entendimento.

- Utilize uma boa arquitetura.
    - [ITCSS](http://www.hugobessa.com.br/posts/ITCSS-uma-maneira-de-pensar-arquiteturas-css/) é uma ótima forma de pensar em como devemos arquitetar nossos estilos.

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
    - Sempre converse com o designer, desde o início do projeto, sobre padronizar componentes. Eles são mais abertos a isso do que você provavelmente acha.

- Evite ter arquivos com mais de 150 linhas.
    - Mais do que isso e você provavelmente está fazendo errado. Abstraia componentes. Sempre.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Referências
- [CSS Guidelines](https://github.com/csswizardry/CSS-Guidelines)
    - Utilize estas diretrizes para escrever CSS da melhor forma. Grande parte deste guia foi baseado nele.
- [Guides por Thoughtbot](https://github.com/thoughtbot/guides/tree/master/style)
    - Este guia também é uma adaptação do Guides da Thoughtbot.

[[⬆︎ Topo]](#sum%C3%A1rio)
