# CSS
> códigos de estilo estilosos

## Sumário
- [Formatação](#formatacao)
- [Seletores](#seletores)
- [Ordenação](#ordenacao)
- [Organização](#organizacao)
- [Referências](#referencias)

[[⬅︎ Voltar para Estilo]](https://github.com/hugobessaa/guides/tree/master/estilo)

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

- Use espaço entre uma propriedade e seu valor.
    ```scss
    .post {
        // bad
        color:#f00;

        // good
        background-color: #00f;
    }
    ```

- Prefira a unidade `em`.
    - Quando usamos `em` nossos componentes podem se adaptar facilmente a mudanças no font-size. Eles são ótimos em breakpoints de `@media` queries também, já que eles são aplicados enquanto damos zoom no browser.

    ```scss
    // bad
    font-size: 32px;
    font-size: 2rem;

    // good
    font-size: 2em;
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

- Use variáveis para cores.
    ```scss
    // bad
    color: #c7f464;

    // good
    $color-lime: #c7f464;
    color: $color-lime;
    ```

- Use o prefixo `color-` em variáveis de cor.
    ```scss
    // bad
    $red: #f00;

    // good
    $color-red: #f00;
    ```

- Use nomes de variável com significado semântico.
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

- Prefira propriedades explícitas.
    - Use `margin-bottom: 0` e `background-color: $color-brand` para ser o mais explícito possível. Use abreviações (`margin: 0`) apenas quando necessário.

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

[[⬆︎ Topo]](#sumario)

## Seletores

- Use seletores por classes
    - Classes são extensíveis e altamente reutilizáveis. Elas são suas melhores amigas no CSS.

- Evite seletores por tags.
    - Seletores por tags são muito específicos. Enquanto estiver desenvolvendo código reutilizável você vai querer ser o mais flexível possível. Use seletores por tags quando você quer estilizar a própria tag (`blockquote`, `a`) ou se você tem uma ótima razão.

- Não use seletores por ID.
    - IDs são muito específicos. Classes não.

- Não especifique seletores mais do que o necessário.
    - Um seletor muito específico não é realmente reutilizável. Se o título (`.title`) muda de uma tag `h2` para `h1` por causa do SEO, por exemplo, você terá que reescrever seu seletor.
    - A abstração é uma das características mais importante de um componente.

    ```scss
    // bad
    h2.title {
        text-transform: uppercase;
    }

    // good
    .title {
        text-transform: uppercase;
    }
    ```

- Evite `!important`
    - Não há problema em usar `!important` em uma classe de ajuda.
    - It is okay to use `!important` on helper classes only. Utilizar `!important` preventivamente é aceitável, como `.error { color: red !important }`, já que você sabe que sempre irá querer que a regra seja aplicada.

    - Usar `!important` reativamente, como para solucionar problemas complicados de especificidade dos estilos, não é recomendado. Revise seu CSS e refatore seu código para combater estes problemas nos seus seletores. Manter seus seletores pequenos e evitar IDs ajudará muito nisso.

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

- Evite aninhar seletores em mais de 4 níveis.
    - É muito fácil criar seletores profundamente aninhados ao utilizar um pré-processador. Seletores profundamente aninhados não são muito reutilizáveis e são lentamente processados pelo browser. Ao usar `Scss` você pode simplesmente indentar os seletores se você estiver tentando espelhar a estruturação do componente no DOM. Mais um ponto para o `Scss`.

    ```scss
    // bad
    .post {
        // ...

        .header {
            // ...

            .info {
                // ...

                .time {
                    // ...

                    a {
                        // ...
                    }
                }
            }
        }
    }

    // good
    .post {
        // ...

        .header {
            // ...
        }

            .info {
                // ...
            }

            .time {
                // ...

                a {
                    // ...
                }
            }
    }
    ```

- Não aninhe em mais de 6 níveis de profundidade.
    - Duas razões a mais do que o último item para não ter seletores profundamente aninhados.

- Prefira seletores `%placeholder` ao usar `@extend`. [(?)](http://csswizardry.com/2014/01/extending-silent-classes-in-sass/).
    ```scss
    // bad
    .post {
        @extend .island;
        // ...
    }

    // good
    .post {
        @extend %island;
        // ...
    }
    ```

[[⬆︎ Topo]](#sumario)

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

- Coloque seletores aninhados por último
    - `.post .title`

- Use ordenação por relevância para propriedades, NÃO alfabética.
    - Para elementos `box`, propriedades de dimensionamento são mais importantes do que aquelas que estilizam o texto. Em elementos `inline` é o oposto. Ao ordenar por relevância, você facilita a leitura das propriedades.

[[⬆︎ Topo]](#sumario)

## Organização
- Use [Normalize](http://necolas.github.io/normalize.css/) como um browser reset. [(?)](http://nicolasgallagher.com/about-normalize-css/)
    - Ele é o padrão do Inuitcss e de muitos outros frameworks.

- Crie arquivos para cada componente.
    - Isso facilita a organização dos seus estilos.

- Use arquivos específicos de páginas para `@import`ar componentes.
    ```scss
    @import "component";
    @import "component";
    ```

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

- Evite código específico em arquivos para páginas.
    - Se você dividir seus componentes em arquivos diferentes você poderá utilizá-los em outras páginas.
    - Antes de escrever um código específico para uma página, se pergunte se isto não é apenas uma variação de algum componente. Se for, introduza a variação ao componente.
    - Sempre converse com o designer, desde o início do projeto, sobre padronizar componentes.

- Avoid having files longer than 100 lines.
    - More than that you are probably doing it wrong. Abstract components. Always.

[[⬆︎ Topo]](#sumario)

## Referências
- [CSS Guidelines](https://github.com/csswizardry/CSS-Guidelines)
    - Utilize estas diretrizes para escrever CSS da melhor forma. Grande parte deste guia foi baseado nele.
- [Guides por Thoughtbot](https://github.com/thoughtbot/guides/tree/master/style)
    - Este guia também é uma adaptação do Guides da Thoughtbot.

[[⬆︎ Topo]](#sumario)
