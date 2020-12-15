# Curso Alura Git

<br/>

### Instalação do Git

Site Oficial: 

* https://git-scm.com

<br/>

### Referências de Consulta

* https://devhints.io/git-log
* https://devhints.io/git-log-format
* https://devhints.io/git-branch

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
    
    

