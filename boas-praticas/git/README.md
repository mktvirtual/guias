# Git
> Git do jeito correto

## Sumário
- [Mantendo um repositório](#mantendo-um-reposit%C3%B3rio)
- [Commits](#commits)
- [Fluxo](#fluxo)
- [Dicas de leitura](#dicas-de-leitura)
- [Referências](#refer%C3%AAncias)

[[⬅︎ Voltar para Boas Práticas]](https://github.com/mktvirtual/guides/tree/master/boas-praticas)

## Mantendo um repositório

- Evite versionar arquivos específicos do seu computador ou processo de desenvolvimento.

- Exclua branches locais e remotas após o `merge`.

- Trabalhe em uma *feature branch*.

- Baixe atualizações dos remotes frequentemente.
    - Prefira `git pull --rebase`, para evitar merges desnecessários.

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
    - O vi já ajuda você a escrever bons commits, quebrando o texto na coluna correta.

- Prefira `git commit --verbose`
    - Poder ver o diff dos arquivos a serem commitados é uma grande facilidade.

- Procure responder as seguintes perguntas na sua mensagem de commit: [(?)](http://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message)
    1. Por que essa alteração é necessária?
    1. Como essa alteração resolve o problema?
    1. Quais os efeitos colaterais desta alteração?

[[⬆︎ Topo]](#sum%C3%A1rio)

## Fluxo de trabalho

1. Crie uma *feature branch* local.
    ```
    git checkout master
    git pull --rebase
    git checkout -b <branch-name>
    ```

1. Realize um *rebase* frequentemente para incorporar mudanças.
    ```
    git fetch origin
    git rebase origin/master
    ```

1. Adicione suas alterações.
    ```
    git add --all
    ```

1. Escreva uma [boa mensagem de commit](#commits).

1. Compartilhe a sua branch.
    ```
    git push origin <branch-name>
    ```

1. Remova sua branch local.
    ```
    git branch --delete <branch-name>
    ```

1. Remova a branch remota.
    ```
    git push origin --delete <branch-name>
    ```

[[⬆︎ Topo]](#sum%C3%A1rio)

## Dicas de leitura

- [git-useful](https://github.com/hugobessaa/git-useful), lista com comandos úteis para usar o git no CLI.
- [Every line of code is always documented](http://mislav.uniqpath.com/2014/02/hidden-documentation/)

[[⬆︎ Topo]](#sum%C3%A1rio)

## Referências

- [Guides por Toughtbot](https://github.com/thoughtbot/guides/tree/master/protocol/git)
    - Este guia também é uma adaptação do Guides da Thoughtbot.
- [git-useful](https://github.com/hugobessaa/git-useful)
    - Uma lista de comandos úteis para utilizar git no Terminal.

[[⬆︎ Topo]](#sum%C3%A1rio)
