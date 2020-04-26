# Reescrevendo o histórico

##### Alterando mensagens de commit

	git commit --amend -m "Minha nova mensagem"

##### Alterar últimos commits
Alterando os três últimos commits

	git rebase -i HEAD~3

O editor de texto será aberto com as linhas representando os três últimos commits.

	pick f7f3f6d changed my name a bit
	pick 310154e updated README formatting and added blame
	pick a5f4a0d added catfile

Altere para edit os commits que deseja realizar alterações.

	edit f7f3f6d changed my name a bit
	pick 310154e updated README formatting and added blame
	pick a5f4a0d added catfile

Feche o editor de texto.

Digite o comando para alterar a mensagem do commit que foi marcado como *edit*.

	git commit –amend -m “Nova mensagem”

Aplique a alteração

	git rebase --continue

**Atenção:** É possível alterar a ordem dos commits ou remover um commit apenas
mudando as linhas ou removendo.


##### Juntando vários commits
Seguir os mesmos passos acima, porém marcar os commtis que devem ser juntados com **squash*
	
##### Remover todo histórico de um arquivo

	git filter-branch --tree-filter 'rm -f passwords.txt' HEAD
	
	
### Bisect
O bisect (pesquisa binária) é útil para encontrar um commit que esta gerando um bug ou uma inconsistência entre uma sequência de commits.

##### Iniciar pequinsa binária

	git bisect start
	
##### Marcar o commit atual como ruim

	git bisect bad

##### Marcar o commit de uma tag que esta sem o bug/inconsistência

	git bisect good vs-1.1

##### Marcar o commit como bom
O GIT irá navegar entre os commits para ajudar a indentificar o commit que esta com o problema. Se o commit atual não estiver quebrado, então é necessário marca-lo como **bom**.

	git bisect good

##### Marcar o commit como ruim
Se o commit estiver com o problema, então ele deverá ser marcado como **ruim**.

 	git bisect bad
 
##### Finalizar a pesquisa binária
Depois de encontrar o commit com problema, para retornar para o *HEAD* utilize:
	
	git bisect reset
 	
