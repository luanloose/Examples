# Branches

O **master** é o branch principal do GIT.

O **HEAD** é um ponteiro *especial* que indica qual é o branch atual. Por padrão, o **HEAD** aponta para o branch principal, o **master**.

##### Criando um novo branch

```GIT
git branch bug-123
```
	
##### Trocando para um branch existente

```GIT
git checkout bug-123
```
	
Neste caso, o ponteiro principal **HEAD** esta apontando para o branch chamado bug-123.

##### Criar um novo branch e trocar 

```GIT
git checkout -b bug-456
```
	
##### Voltar para o branch principal (master)

```GIT
git checkout master
```
	
##### Resolver merge entre os branches

```GIT
git merge bug-123
```
	
Para realizar o *merge*, é necessário estar no branch que deverá receber as alterações. O *merge* pode automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas.

A mensagem indicando um *merge* manual será:

	Automerging meu_arquivo.txt
	CONFLICT (content): Merge conflict in meu_arquivo.txt
	Automatic merge failed; fix conflicts and then commit the result.


##### Apagando um branch

```GIT
git branch -d bug-123
```

##### Listar branches 

###### Listar branches

```GIT
git branch
```

###### Listar branches com informações dos últimos commits

```GIT
git branch -v
```

###### Listar branches que já foram fundidos (merged) com o **master**

```GIT
git branch --merged
```

###### Listar branches que não foram fundidos (merged) com o **master**

```GIT
git branch --no-merged
```

##### Criando branches no repositório remoto

###### Criando um branch remoto com o mesmo nome

```GIT
git push origin bug-123
```

###### Criando um branch remoto com nome diferente

```GIT
git push origin bug-123:new-branch
```

##### Baixar um branch remoto para edição

```GIT
git checkout -b bug-123 origin/bug-123
```


##### Apagar branch remoto

```GIT
git push origin:bug-123
```

### Rebasing

Fazendo o **rebase** entre um o branch bug-123 e o master.

```GIT
git checkout experiment
```

```GIT	
git rebase master
```
	

Mais informações e explicações sobre o [Rebasing](http://git-scm.com/book/en/Git-Branching-Rebasing)

### Stash

Para alternar entre um branch e outro é necessário fazer o commit das alterações atuais para depois trocar para um outro branch. Se existir a necessidade de realizar a troca sem fazer o commit é possível criar um **stash**. O Stash como se fosse um branch temporário que contem apenas as alterações ainda não commitadas.

##### Criar um stash

```GIT	
git stash
```
	
##### Listar stashes

```GIT
git stash list
```

##### Voltar para o último stash

```GIT
git stash apply
```

##### Voltar para um stash específico

```GIT	
git stash apply stash@{2}
```
	
Onde **2** é o indíce do stash desejado.

##### Criar um branch a partir de um stash

```GIT
git stash branch meu_branch
```
