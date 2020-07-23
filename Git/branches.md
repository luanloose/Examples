# Git Examples

## Branches

O **master** é o branch principal do GIT.

O **HEAD** é um ponteiro que indica qual é o branch atual. Por padrão ele fica no **master**.

## Criando um novo branch

```GIT
git branch teste
```

## Trocando para um branch existente

```GIT
git checkout bugfix
```

Neste caso, o **HEAD** esta apontando para o branch bugfix.

## Criar um novo branch e trocar

```GIT
git checkout -b bug-456
```

## Voltar para o branch principal (master)

```GIT
git checkout master
```

## Resolver merge entre os branches

```GIT
git merge teste
```

Para realizar o merge entre 2 branchs, você deve estar no branch que deverá receber as atualizações. O merge pode automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas.

Exemplo de mensagem do merge manual:

```CMD
Automerging codigo.php
CONFLICT (content): Merge conflict in codigo.php
Automatic merge failed; fix conflicts and then commit the result.
```

## Apagando um branch

```GIT
git branch -d teste
```

## Listar branches

* Simples

```GIT
git branch
```

* Com informações dos últimos commits

```GIT
git branch -v
```

* Que já sofreram merge com o master

```GIT
git branch --merged
```

* Que não sofreram merge com o master

```GIT
git branch --no-merged
```

## Criando branches no repositório remoto

* Com o mesmo nome

```GIT
git push origin teste
```

* Com nome diferente

```GIT
git push origin teste:new-branch
```

## Baixar um branch remoto para edição

```GIT
git checkout -b teste origin/teste
```

## Apagar branch remoto

```GIT
git push origin:teste
```

### Rebasing

Fazendo o **rebase** entre um o branch teste e o master.

```GIT
git checkout experiment
```

```GIT
git rebase master
```

Mais informações e explicações sobre o [Rebasing](http://git-scm.com/book/en/Git-Branching-Rebasing)

### Stash

Para alternar entre um branch e outro é necessário fazer o commit das alterações atuais para depois trocar para um outro branch. Se existir a necessidade de realizar a troca sem fazer o commit é possível criar um **stash**. O Stash como se fosse um branch temporário que contem apenas as alterações ainda não commitadas.

## Criar um stash

```GIT
git stash
```

## Listar stashes

```GIT
git stash list
```

## Voltar para o último stash

```GIT
git stash apply
```

## Voltar para um stash específico

```GIT
git stash apply stash@{2}
```

Onde **2** é o indíce do stash desejado.

## Criar um branch a partir de um stash

```GIT
git stash branch meu_branch
```
