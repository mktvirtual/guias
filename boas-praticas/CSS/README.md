# CSS
> CSS também pode ser reutilizável e modular

## Sumário
- [Formatação](#formata%C3%A7%C3%A3o)
- [Seletores](#seletores)
- [Ferramentas](#ferramentas)
- [Dicas de leitura](#dicas-de-leitura)
- [Referências](#refer%C3%AAncias)

[[⬅︎ Voltar para Boas Práticas]](https://github.com/mktvirtual/guides/tree/master/boas-praticas)

## Formatação

- Prefira propriedades explícitas.
    - Use `margin-bottom: 0` e `background-color: $color-brand` para ser o mais explícito possível. Use abreviações (`margin: 0`) apenas quando necessário.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Seletores

- Use seletores por classes.
    - Classes são extensíveis e altamente reutilizáveis. Elas são suas melhores amigas no CSS. Use-as e diga adeus ao `!important`.

- Evite seletores por tags.
    - Seletores por tags são muito específicos. Enquanto estiver desenvolvendo código reutilizável você vai querer ser o mais flexível possível. Use seletores por tags quando você quer estilizar a própria tag (`blockquote`, `a`) ou se você tem uma ótima razão.

- Não use seletores por ID.
    - IDs são muito específicos. Classes não. Não existe uma boa razão para utilizar seletores por IDs. Se sentindo sem opção, obrigado a usar ID? Talvez [esse post](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/) te ajude.

- Não especifique seletores mais do que o necessário.
    - Um seletor muito específico não é realmente reutilizável. Se o título (`.title`) muda de uma tag `h2` para `h1` por causa do SEO, por exemplo, você terá que reescrever seu seletor.
    - A abstração é uma das características mais importante de um componente.

    ```scss
    // ruim
    h2.title {
        text-transform: uppercase;
    }

    // bom
    .title {
        text-transform: uppercase;
    }
    ```

- Evite `!important`.
    - Não há problema em usar `!important` em uma classe de ajuda.

    - Utilizar `!important` preventivamente é aceitável, como `.error { color: red !important }`, já que você sabe que sempre irá querer que a regra seja aplicada.

    - Usar `!important` reativamente, como para solucionar problemas complicados de especificidade dos estilos, não é recomendado. Revise seu CSS e refatore seu código para combater estes problemas nos seus seletores. Manter seus seletores pequenos e evitar IDs ajudará muito nisso.

    - [Conheça algumas formas para "hackear" a especificidade no CSS](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/).

- Evite aninhar seletores em mais de 4 níveis.
    - É muito fácil criar seletores profundamente aninhados ao utilizar um pré-processador. Seletores profundamente aninhados não são muito reutilizáveis e são lentamente processados pelo browser. Ao usar `Scss` você pode simplesmente indentar os seletores se você estiver tentando espelhar a estruturação do componente no DOM. Mais um ponto para o `Scss`.

    ```scss
    // ruim
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

    // bom
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
    // ruim
    .post {
        @extend .island;
        // ...
    }

    // bom
    .post {
        @extend %island;
        // ...
    }
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Ferramentas

- Use [Normalize](http://necolas.github.io/normalize.css/) como um browser reset. [(?)](http://nicolasgallagher.com/about-normalize-css/)
    - Ele é o padrão do Inuitcss e de muitos outros frameworks.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Dicas de leitura

- [Hacks for dealing with specificity](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/)
- [The problems with 'Crafting' code](http://csswizardry.com/2013/11/the-problems-with-crafting-code/)

[[⬆︎ Topo]](#sum%C3%A1rio)

## Referências
- [CSS Guidelines](https://github.com/csswizardry/CSS-Guidelines)
    - Utilize estas diretrizes para escrever CSS da melhor forma. Grande parte deste guia foi baseado nele.
- [Guides por Thoughtbot](https://github.com/thoughtbot/guides/tree/master/style)
    - Este guia também é uma adaptação do Guides da Thoughtbot.

[[⬆︎ Topo]](#sum%C3%A1rio)
