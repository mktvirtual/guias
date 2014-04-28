# CSS
> code style for cascading style sheets

## Table of Contents
- [Formating](#formatting)
- [Selectors](#selectors)
- [Order](#order)
- [Organization](#organization)
- [References](#reference)

[[⬅︎ Back to Style]](https://github.com/hugobessaa/guides/tree/master/style)

## Formatting
- Use Sass.
    - Sass give us the power to write extensible CSS with variables, conditionals, functions and stuff. Use it.

- Prefer the *Scss* syntax.
    - *Scss* make you type more as it needs symbols and `@include` instead of `+`, but it can make your code way easier to read and understand. It is also the only flavor of Sass that is compatible with [libsass](https://github.com/hcatlin/libsass), a very fast Sass compiler written in C.

- Use hyphens when naming mixins, extends, classes, functions, and variables.
    ```scss
    // bad
    $colorUser = #f00;
    $color_user = #f00;

    // good
    $color-user = #f00;
    ```

- Use space between property and value.
    ```scss
    .post {
        // bad
        color:#f00;

        // good
        background-color: #00f;
    }
    ```

- `Sass` Use a blank line above selector that has styles.
    ```sass
    // bad
    .post
        color: #f00
        .title
            font-size: 3em

    // good
    .post
        color: #f00

        .title
            font-size: 3em

    ```

- Prefer `em` unit.
    - when using `em` units your components can easily adapt to font-size changes. They are great for `@media` queries breakpoints too, as they are applied while zooming.

    ```scss
    // bad
    font-size: 32px;
    font-size: 2rem;

    // good
    font-size: 2em;
    ```

- Prefer hex color codes, when possible.
    ```scss
    // bad
    color: white;
    color: rgb(0, 0, 0);

    // good
    color: #fff;
    color: rgba(0, 0, 0, 0.7);
    ```
- Use color variables.
    ```scss
    // bad
    color: #c7f464;

    // good
    $color-lime: #c7f464;
    color: $color-lime;
    ```
- Use `color-` prefix in color variables.
    ```scss
    // bad
    $red: #f00;

    // good
    $color-red: #f00;
    ```

- Use meaningful variable names.
    ```scss
    // bad
    $color-red: #f00;
    color: $color-red;

    // good
    $color-red: #f00;
    $color-text: $color-red;
    color: $color-text;
    ```

- Use a space between selector and `{`.
    ```scss
    // bad
    .post{
        color: $color-text;
    }

    // good
    .post {
        color: $color-text;
    }
    ```

- Use only lowercase, including colors.
    ```scss
    // bad
    color: #FFF;

    // good
    color: #fff;
    ```

- Don't add a unit specification after 0 values, unless required by a mixin.
    ```scss
    // bad
    margin: 0px;

    // good
    margin: 0;
    ```

- Prefer explicit properties.
    - Use `margin-bottom: 0` and `background-color: $color-white` to be as explicit as possible in your styles. Just use shorthand (e.g. `margin: 0` and `background: red`) when necessary.

- `Scss` Use trailing semi-colons.
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

[[⬆︎ Back to Top]](#table-of-contents)

## Selectors
- Use class selectors.
    - Classes are extensible and highly reusable. They are your best friends when developing great CSS.

- Avoid tag selectors.
    - Tag selectors are too specific. When developing reusable code you want to be as flexible as possible. Use than if you want to style the tag itself or if you have a really good reason.

- Don't use id selectors.
    - IDs are too specific. Classes aren't.

- Don't over-qualify selectors.
    - An over-qualified selector isn't really reusable. If a `.title` tag changes from `h2` to `h1` because of SEO reasons, for example, you will have to rewrite your selector.

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

- Avoid `!important` rule.
    - It is okay to use `!important` on helper classes only. To add `!important` preemptively is fine, e.g. `.error { color: red !important }`, as you know you will always want this rule to take precedence.

    - Using `!important` reactively, e.g. to get yourself out of nasty specificity situations, is not advised. Rework your CSS and try to combat these issues by refactoring your selectors. Keeping your selectors short and avoiding IDs will help out here massively.

- Don't eat vowels.
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

- Avoid nesting more than 4 selectors deep.
    - It's very easy to create deeply nested selectors when using a CSS pre-processor. Deeply nested selectors are not very reusable and slow to be processed by browsers. When using *Scss* you can simply indent the selectors if you are trying to mirror the DOM.

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
- Don't nest more than 6 selectors deep.
    - Two more reasons than the last item to not have deeply nested selectors.

- Prefer `%placeholder` selectors to `@extend`. [Here's why](http://csswizardry.com/2014/01/extending-silent-classes-in-sass/).
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

[[⬆︎ Back to Top]](#table-of-contents)

## Order
- Place `@extends` and `@includes` at the top of your declaration list.
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

- Place concatenated selectors second.
    - `.post.featured`

- Place pseudo states and elements third.
    - `.post:hover`

- Place nested selectors last.
    - `.post .title`

- Use relevance ordering for properties, NOT alphabetical.
    - For box elements, sizing properties are more important than text properties. In inline elements it's the opposite. By ordering properties by relevance you make it easy to read the most important things first.

[[⬆︎ Back to Top]](#table-of-contents)

## Organization
- Use [Normalize](http://necolas.github.io/normalize.css/) as a browser reset.
    - It's the default of Inuitcss and many other frameworks.

- Create files for each component.
    - This introduces a better organization to our styles.

- Use page specific files to `@import` components.
    ```scss
    @import "component";
    @import "component";
    ```

- Divide blocks of code with comments.
    ```scss
    /*------------------------------------*\
        #POST
    \*------------------------------------*/

    .post {
        margin: 10px 0;
        // ...
    }
    ```

- Avoid hard coding styles in page specific files.
    - If you split your components in different files you can use them in other pages.

- Avoid having files longer than 100 lines.
    - More than that you are probably doing it wrong. Abstract components. Always.

[[⬆︎ Back to Top]](#table-of-contents)

## References
- [CSS Guidelines](https://github.com/csswizardry/CSS-Guidelines)
    - Use these guidelines to write better CSS. Most of this guide was based on it.
- [Guides by Thoughtbot](https://github.com/thoughtbot/guides/tree/master/style)
    - This guide is also an adaptation of Thoughtbot's Guides.

[[⬆︎ Back to Top]](#table-of-contents)
