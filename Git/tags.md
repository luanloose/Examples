# Tags

##### Criando uma tag

```GIT
git tag vs-1.1
```

##### Criando uma tag anotada

```GIT
git tag -a vs-1.1 -m "Minha versão 1.1"
```

##### Criando uma tag assinada
Para criar uma tag assinada é necessário uma chave privada (GNU Privacy Guard - GPG).

```GIT
git tag -s vs-1.1 -m "Minha tag assinada 1.1"
```

##### Criando tag a partir de um commit (hash)

```GIT
git tag -a vs-1.2 9fceb02
```

##### Criando tags no repositório remoto

```GIT
git push origin vs-1.2
```

##### Criando todas as tags locais no repositório remoto

```GIT
git push origin --tags
```
