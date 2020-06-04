# Repositórios

## Criar novo repositório

```GIT
git init
```

## Verificar estado dos arquivos/diretórios

```GIT
git status
```

## Adicionar arquivo/diretório (staged area)

* Arquivo em específico

```GIT
git add meu_arquivo.txt
```

* Diretório em específico

```GIT
git add meu_diretorio
```

* Todos os arquivos/diretórios

```GIT
git add .
```

* Arquivo listado no .gitignore (geral ou do repositório)

```GIT
git add -f arquivo_no_gitignore.txt
```

## Comitar arquivo/diretório

* Arquivo

```GIT
git commit arquivo.txt
```

* Vários arquivos

```GIT
git commit arquivo.txt outro_arquivo.txt
```

* Informando mensagem

```GIT
git commit arquivo.txt -m "mensagem no commit"
```

## Remover arquivo/diretório

* Arquivo

```GIT
git rm arquivo.txt
```

* Diretório

```GIT
git rm -r diretorio
```

## Repositório Remoto

* Adicionar um repositório remoto

```CMD
$ git remote add origin https://github.com/user/repo.git
# Defina um novo remote

$ git remote -v
# Verifique  o novo remote
> origin  https://github.com/user/repo.git (fetch)
> origin  https://github.com/user/repo.git (push)
```

Possivel erro

* O remote name já existe:

```CMD
$ git remote add origin git@github.com:luanloose/Examples.git
> fatal: remote origin already exists.
```

> Para resolver você pode renomear ou excluir o repositório remoto

## Exibir os repositórios remotos

```GIT
git remote
```

```GIT
git remote -v
```

## Vincular repositório local com um repositório remoto

```GIT
git remote add origin git@github.com:luanloose/Examples.git
```

## Exibir informações dos repositórios remotos

```GIT
git remote show origin
```

## Renomear um repositório remoto

```GIT
git remote rename origin examples
```

## Desvincular um repositório remoto

```GIT
git remote rm examples
```

## Enviar arquivos/diretórios para o repositório remoto

O primeiro **push** de um repositório deve conter o nome do repositório remoto e o branch.

```GIT
git push -u origin master
```

Os demais **pushes** não precisam dessa informação

```GIT
git push
```

## Atualizar repositório local de acordo com o repositório remoto

## Arquivos no branch atual

```GIT
git pull
```

## Buscar as alterações, mas não aplica-las no branch atual

```GIT
git fetch
```

## Clonar um repositório remoto já existente

```GIT
git clone git@github.com:luanloose/Examples.git
```
