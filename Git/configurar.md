# Configuração

### Geral

As configurações do GIT são armazenadas no arquivo **.gitconfig** localizado dentro do diretório do usuário do Sistema Operacional (Ex.: Windows: C:\Users\Documents and Settings\Leonardo ou *nix /home/leonardo).

As configurações realizadas através dos comandos abaixo serão incluídas no arquivo citado acima.

##### Setar usuário

```GIT
git config --global user.name "Leonardo Comelli"
```

##### Setar email

```GIT
git config --global user.email leonardo@software-ltda.com.br
```

##### Setar editor

```GIT
git config --global core.editor vim
```

##### Setar ferramenta de merge

```GIT
git config --global merge.tool vimdiff
```


##### Setar arquivos a serem ignorados

```GIT
git config --global core.excludesfile ~/.gitignore
```

##### Listar configurações

```GIT
git config --list
```
