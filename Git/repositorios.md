# Repositórios

### Criar novo repositório

```GIT
git init
```

### Verificar estado dos arquivos/diretórios

```GIT
git status
```

### Adicionar arquivo/diretório (staged area)

##### Adicionar um arquivo em específico

```GIT
git add meu_arquivo.txt
```

##### Adicionar um diretório em específico

```GIT
git add meu_diretorio
```

##### Adicionar todos os arquivos/diretórios

```GIT	
git add .	
```

##### Adicionar um arquivo que esta listado no .gitignore (geral ou do repositório)

```GIT	
git add -f arquivo_no_gitignore.txt
```

### Comitar arquivo/diretório

##### Comitar um arquivo

```GIT	
git commit meu_arquivo.txt
```

##### Comitar vários arquivos

```GIT
git commit meu_arquivo.txt meu_outro_arquivo.txt
```

##### Comitar informando mensagem

```GIT
git commit meuarquivo.txt -m "minha mensagem de commit"
```

### Remover arquivo/diretório

##### Remover arquivo

```GIT
git rm meu_arquivo.txt
```

##### Remover diretório

```GIT
git rm -r diretorio
```

## Repositório Remoto

### Adicionar um repositório remoto
	$ git remote add origin https://github.com/user/repo.git
	# Defina um novo remote

	$ git remote -v
	# Verifique  o novo remote
	> origin  https://github.com/user/repo.git (fetch)
	> origin  https://github.com/user/repo.git (push)


Pode acontecer o seguinte problema

* O remote name já existe: 

		Esse erro significa que você tentou adicionar um remote com um nome que já existe no repositório local:

		$ git remote add origin https://github.com/octocat/Spoon-Knife
		> fatal: remote origin already exists.

> Para resolver você pode renomear ou excluir o repositório remoto

### Exibir os repositórios remotos

```GIT
git remote
```

```GIT	
git remote -v
```

### Vincular repositório local com um repositório remoto

```GIT
git remote add origin git@github.com:leocomelli/curso-git.git
```

### Exibir informações dos repositórios remotos

```GIT
git remote show origin
```

### Renomear um repositório remoto 

```GIT
git remote rename origin curso-git
```

### Desvincular um repositório remoto

```GIT	
git remote rm curso-git
```

### Enviar arquivos/diretórios para o repositório remoto

O primeiro **push** de um repositório deve conter o nome do repositório remoto e o branch.

```GIT
git push -u origin master
```

Os demais **pushes** não precisam dessa informação

```GIT
git push
```

### Atualizar repositório local de acordo com o repositório remoto

##### Atualizar os arquivos no branch atual

```GIT
git pull
```

##### Buscar as alterações, mas não aplica-las no branch atual

```GIT
git fetch
```

### Clonar um repositório remoto já existente

```GIT
git clone git@github.com:leocomelli/curso-git.git
```
