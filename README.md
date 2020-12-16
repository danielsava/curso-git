# Git

<br/>

### Instalação do Git

Siga as instruções do site oficial: 

* https://git-scm.com

<br/>

### Referências de Consulta

* https://devhints.io/git-log
* https://devhints.io/git-log-format
* https://devhints.io/git-branch
* https://git-school.github.io/visualizing-git

<br/>

### Comandos Básicos

##
Para conferir a instalação:

    git --version
    
##  
Para iniciar um repositório, dentro  do diretório desejado:

    git init
    
## 
Para saber informações sobre o repositório atual:
    
    git status

<br/>

### Configurações

Segue abaixo alguns comando, de exemplo, para visualizar ou alterar as configurações do git.

<br/> 

Para visualizar todas as configurações do git:

    git config -l    

<br/>

Para visualizar as configurações que serão aplicadas de forma global, ou seja, em todos os repositórios
    
    git config --global -l  

<br/>
    
Para visualizar somente as configurações do repositório atual  

    git config --local -l

<br/>

Para visualizar um atributo específico:

    git config user.email
    
Ou

    git config user.name

       
#       
Para alterar alguma opção de configuração, basta:

    git config --local user.name "Asdrubal Tibúrcio"
    git config --local user.email "asdrubal.tiburcio@umbrella.ti"

<br/>

### Versionando Arquivos

Adicionar arquivos para o versionamento:
    
    git add .
    
Ou 

    git add <nome_arquivo>
    
Ou 

    git add *.java    
    
#
Submetendo arquivos versionados:

    git commit -m "Mensagem ..."
    
<br/>
 
### Logs 
 
Segue abaixo exemplos do comando log para visualizar o histórico e as informações dos committers, e alterações que foram realizadas nos arquivos.

    git log  
_ 

    git log --oneline
        
_ 

    git log --graph
    
_ 

    git log --graph --oneline
    
_ 

    git log --graph --oneline --date=relative
    
_

    git log -p (visualiza as alterações dos arquivos)
    
    
<br/>

O comando de log possui diversas opções, inclusive possibilita formatar e personalizar as mensagem de log. 
Para saber mais opções deste comando, tem links no tópico de referência ou execute o comando help:

    git log --help
    
<br/>


### Ignorando arquivos

Através do arquivos `.gitignore` é possível configurar quais arquivos e/ou diretório devem ser ignorados pelo git.


#
Para ignorar um arquivo, basta adicioná-lo ao arquivo:

    ide-config.conf
 
#   
Ou para ignorar os arquivos de um determinado diretório:

    ide/
    
<br/>
    
    
### Criando um Repositório Remoto

Com o git instalado, escolha um diretório que será utilizado para armazenar as alterações dos arquivos. Este repositório 
por ser utilizado, por outros repositórios, com um repositório remoto.

Pelo fato de ser um repositório, que podemos dizer, mais `simples`, basta utilizar a flag `--bare` no comando init, conforme
mostrado abaixo:

    git init --bare
    
O caminho deste repositório, criado acima, pode ser configurado em outras repositórios como repositório remoto. 

<br/>

### Configurando Repositório Remoto

Dentro do repositório desejado, digite o comando abaixo para listar os repositórios remotos:

    git remote
    
Ou

    git remote -v  (verbose)

Caso a saída dos comandos acima seja vazia, significa que o repositório atual nãop possui nenhum repositório remoto configurado.

#
Para adicionar um repositório remoto, basta executar o comando abaixo (utilizado como exemplo):

    git remote add local C:/Users/ALURA/Documents/git-e-github/servidor/
    
O `local` é o nome dado à varíavel que irá armazenar o endereço do repositório remoto, que pode ser um `caminho de rede`, 
um outro `diretório` na máquina local, ou uma `url`. 

Por padrão, adota-se o nome de `origin` como nome de variável, ou aliás, para o endereço dos repositórios remotos.


#
Caso deseje alterar o nome do repositório remoto, basta utilizar o comando `git remote rename`:

    git remote rename local novo_nome
    
Exemplo:

    git remote rename local origin

<br/>

### `Clonando` Repositórios Remotos

Utilizando o repositório remoto criado no exemplo acima, ele será clonado no diretório 'projeto':

    git clone /C/Users/ALURA/Documents/git-e-github/servidor/ projeto
        
Ou caso deseje clonar para o diretório atual:
    
    git clone /C/Users/ALURA/Documents/git-e-github/servidor/
 
<br/>  
    
### `Empurrando` alterações para Repositórios Remotos

Para enviar os commits locais para um repositório remoto, é utilizado o comando push.  Utilizando o exemplo adotado até o momento, 
onde configuramos um repositório remoto com nome de `local`, será utilziado a seguinte sintaxe no comando `push`:

    git push local master

Ou, caso deseje setar o repositório `local` como `default`, executar o comando push com a opção `- u`:

    git push -u local master
    
Desta forma, toda vez que estiver na `branch master` basta executar `git push` que os commits serão enviados para o repositório
remoto `local`.

Alguns desenvolvedores, por questões de controle, preferem executar o comando completo:

    git push <alias_sever_remote> <nome_branch>
    
O mesmo se aplica ao comando `pull`. 

    git push <alias_sever_remote> <nome_branch>

<br/>    
    
### Buscando alterações do Repositório Remoto

Com repositório remoto já configurado com o nome `local`, o comando abaixa busca as alterações da branch `master`.

    git pull local master
    
Poderia ser qualquer servidor remoto configurado ou qualquer branch existente no repositório remoto `local`.

<br/>

### Branch

Para listar as branchs que o repositório possui:

    git branch
    
Ou 

    git branch -l (listar)
    
#
Para criar uma nova branch:

    git branch <nome_branch> 
   
    
#    
Para mudar para a nova branch criada, utilize o comando `checkout`:

    git checkout <nome_branch>


O comando `checkout` com a flag `-b` cria uma nova branch e muda para branch criada:

    git checkout -b funcionalidade_x
    
#
Para remover uma branch:

    git branch -d funcionalidade_x
    
#
Para enviar as alterações da branch para o repositório remoto:

    git push origin funcionalidade_x

<br/>

### Merge Branch

O comando `merge` irá atualizar a branch atual com as alterações de uma outra branch. Portanto, na branch que deseja
atualizar, executar o `merge` informando o nome da branch que deseja bsucar as alterações.

    git merge funcionalidade_x
    
Exemplo: a seguinte de comando abaixo irá atualizar a branch `master` com as modificações feitas na branch `titulo`

    git checkout master
    git merge titulo


### Merge vs Rebase

O `merge` junta todos commits da branch de origem e unifica-os em um único commit na branch de destino, no qual 
podemos chamar de `merge commit`. O `rebase` busca todos os commits da branch de destino e aplica na branch de destino.
A sintaxe do comando `rebase` é a mesma do `merge`. 

    git rebase <nome_branch_origem>
    
<br/>

### Desfazendo alterações

#### Checkout

Caso queira desfazer alterações `not staged` (cor vermelha no `git status`) de um determinado arquivo:

    git checkout -- <nome_arquivo>

#### Reset    

Para desfazer alterações `staged` (cor verde no `git status`), que estão prontas pra serem comitadas, de um determinado
arquivo utilize o `reset`. O reset altera o status do arquivo de `staged` (verde) para `not staged` (vermelho), 
por isso é necessário executar, posteriormente, o `checkout` para concluir que as alterações sejam desfeitas:  

    git reset HEAD <nome_arquivo>
    git checkout -- <nome_arquivo>

#### Revert

O rever altera as modificações de um determinado commit. Para isso, basta informar a Hash de identificaão do commit que
será desfeito:

    git revert <hash_commit>

Exemplo:

    git revert 974498e8fb0920b4d2252c2a3448ea1c98be283e
    
O `revert` irá gerar um <b> novo commit </b> desfazendo as alterações do commit informado.
   
    
<br/>
 
### Guardando alterações temporariamente (stash)

As alterações `not staged` (vermelhas) podem ser separadas, guardadas, em um local temporário para que possam posteriormente
serem recuperadas. Este é o conceito de `stash` no GIT. Para tanto, a utilização do comando é bastante simples.

    git stash
    
Dessa forma, todas as alterações `not staged` foram `guardadas` em um lugar temporário. Para listar o que está salvo no `stash`:

    git stash list
    
Para <b> recuperar </b> as modificações salvas no stash, podem ser utilizados os seguintes comandos:

#### Stash Apply

    git stash apply <numr_identificacao_stash>

O número de identificação da stash pode ser obtida através do `git stash list`. O `apply` <b> não remove </b> a stash 
recuperada. Para remover:

    git stash drop <numr_identificacao_stash>     


#### Stash Pop    

O comando `stash pop` recupera a <b> ÚLTIMA </b> alteração adicionada e a remove do `stash`. Portanto, bastando para isso:

    git stash pop
    
O comando irá buscar a última alteração inserida no stash, e faz um merge com os arquivos que foram modificados. 

    