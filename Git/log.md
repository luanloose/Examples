# Visualizar histórico

##### Exibir histórico

```GIT	
git log
```

##### Exibir histórico com diff das duas últimas alterações

```GIT
git log -p -2
```

##### Exibir resumo do histórico (hash completa, autor, data, comentário e qtde de alterações (+/-))

```GIT
git log --stat
```

##### Exibir informações resumidas em uma linha (hash completa e comentário)

```GIT
git log --pretty=oneline
```

##### Exibir histórico com formatação específica (hash abreviada, autor, data e comentário)

```GIT
git log --pretty=format:"%h - %an, %ar : %s"
```

* %h: Abreviação do hash;
* %an: Nome do autor;
* %ar: Data;
* %s: Comentário.

Verifique as demais opções de formatação no [Git Book](http://git-scm.com/book/en/Git-Basics-Viewing-the-Commit-History)

##### Exibir histório de um arquivo específico

```GIT
git log -- <caminho_do_arquivo>
```

##### Exibir histórico de um arquivo específico que contêm uma determinada palavra

```GIT
git log --summary -S<palavra> [<caminho_do_arquivo>]
```

##### Exibir histórico modificação de um arquivo

```GIT
git log --diff-filter=M -- <caminho_do_arquivo>
```

* O <D> pode ser substituido por: Adicionado (A), Copiado (C), Apagado (D), Modificado (M), Renomeado (R), entre outros.

##### Exibir histório de um determinado autor

```GIT
git log --author=usuario
```

##### Exibir revisão e autor da última modificação de uma bloco de linhas

```GIT
git blame -L 12,22 meu_arquivo.txt
```

### Desfazendo operações

##### Desfazendo alteração local (working directory)
Este comando deve ser utilizando enquanto o arquivo não foi adicionado na **staged area**. 

```GIT
git checkout -- meu_arquivo.txt
```

##### Desfazendo alteração local (staging area)
Este comando deve ser utilizando quando o arquivo já foi adicionado na **staged area**.

```GIT
git reset HEAD meu_arquivo.txt
```

Se o resultado abaixo for exibido, o comando reset *não* alterou o diretório de trabalho. 

	Unstaged changes after reset:
	M	meu_arquivo.txt

A alteração do diretório pode ser realizada através do comando abaixo:

```GIT	
git checkout meu_arquivo.txt
```

