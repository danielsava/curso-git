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


### Branch

Para listar as branchs que o repositório possui:

    git branch
    
Ou 

    git branch -l (listar)

<br/>
    
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


    