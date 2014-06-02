# Git
> Git do jeito correto

## Sumário
- [Mantendo um repositório](#mantendo-um-reposit%C3%B3rio)
- [Commits](#commits)
- [Referências](#refer%C3%AAncias)

[[⬅︎ Voltar para Boas Práticas]](https://github.com/mktvirtual/guides/tree/master/boas-praticas)

## Mantendo um repositório

- Evite versionar arquivos específicos do seu computador ou processo de desenvolvimento.

- Exclua branches locais e remotas após o merge.

- Trabalhe em uma *feature branch*.

- Baixe atualizações dos remotes frequentemente.

[[⬆︎ Topo]](#sum%C3%A1rio)

## Commits

- Use mensagens em inglês.

- Escreva uma boa mensagem de commit. [(?)](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
    - Formato de exemplo:
        ```
        Present-tense summary under 50 characters

        Write more explanatory text to documment your changes.

        * More information about commit (under 72 characters).
        * More information about commit (under 72 characters).

        http:://project.management-system.com/ticket/123
        ```

- Evite utilizar `git commit -m ""`.
    - Este comando impede que você escreva mensagens com múltiplas linhas com facilidade. Sem o `-m`, você escreverá suas mensagens no vi.
    - Prefira `git commit --verbose`

- Procure responder as seguintes perguntas na sua mensagem: [(?)](http://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message)
    1. Por que essa alteração é necessária?
    1. Como essa alteração resolve o problema?
    1. Quais os efeitos colaterais desta alteração?

[[⬆︎ Topo]](#sum%C3%A1rio)

## Referências

- [Guides/protocol/git por Toughtbot](https://github.com/thoughtbot/guides/tree/master/protocol/git)

[[⬆︎ Topo]](#sum%C3%A1rio)
