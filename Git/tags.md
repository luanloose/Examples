# Tags

* ### Criar uma tag

```GIT
git tag vs-1.0
```

* ### Criar uma tag anotada

```GIT
git tag -a vs-1.0 -m "versão 1.0"
```

* ### Criar uma tag assinada
Para criar uma tag assinada é necessário uma chave privada (GNU Privacy Guard - GPG).

```GIT
git tag -s vs-1.0 -m "Primeira tag assinada 1.0"
```

* ### Criar tag a partir de um commit (hash)

```GIT
git tag -a vs-1.0 fc76014
```

* ### Criar tags no repositório remoto

```GIT
git push origin vs-1.2
```

* ### Criar todas as tags locais no repositório remoto

```GIT
git push origin --tags
```
