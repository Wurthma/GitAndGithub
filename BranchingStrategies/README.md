# Branching Strategies, Conflicts, and Pull Requests

## Unindo commits e cherry-pick

Quando temos vários commits, podemos uni-los com o comando:

`git rebase -i HEAD~3`

O comando acima vai unificar os ultimos 3 commits.

Após isso será exibido uma tela onde deveremos fazer o 'squash' dos commits e o 'pick' do commit que queremos manter.

Finalizando, podemos escrever uma mensagem e usar o `:x` para salvar.

`git cherry-pick 2efd26a` irá trazer apenas as alterações do commit 2efd26a para a branch atual.

## Localizando alterações nos commits

Podemos usar `git bisect start` para navegar entre os commits e localizar uma alteração especifica.

Após a execução do **bisect start** precisamos informar o commit inicial e final onde faremos a busca:

	1- `git bisect bad HEAD` -> HEAD para pegar o commit atual da branch ou podemos usar um commit especifico
	2- `git bisect good c2a801e` -> commit final que limitara a busca.
	
O git navegará entre os commits e você pode usar `git bisect bad` para informar que ainda não encontrou as alterações que está procurando e `git bisect good` para informar que a alteração já foi encontrada.

`git bisect reset` irá finalizar a busca.

Ou para encontrar responsáveis:

`git blame <fileName>` nos mostra o responsável por cada linha do arquivo.

## Gitflow

Imagens com exemplos do gitflow

## Ferramentas

Abaixo algumas ferramentas que podem ajudar no versionamento com Git:

- GitKraken 
- GitHub Desktop
- Git Cola
