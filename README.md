# Minicurso 'Criando meu primeiro repositório no GitHub' - Palco Multiuso PyLadies DF CPBSB6

Este repositório contém o tutorial com o passo a passo para a criação do seu primeiro repositório no GitHub. Se encontrar erros ou tiver sugestões de melhorias, sinta-se a vontade para comentar! 

Não estava na oficina e tem dúvidas sobre o que é Git? Aqui temos o [link](https://www.canva.com/design/DAFdTK3jMBo/m71Og_6jedV5fuMzctV5uQ/edit?utm_content=DAFdTK3jMBo&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton) da apresentação onde explicamos o que é Git e GitHub. Sinta-se a vontade para acessá-lo e descobrir mais sobre o assunto! 

## 1. Crie sua conta no GitHub

* Acesse o [GitHub](https://www.github.com) e clique em 'Sign up for GitHub'. 

* Insira as suas informações e customize o seu perfil.

## 2. Instalando o Git na sua máquina: 

* Acesse o [endereço](https://git-scm.com/downloads) e faça download do Git de acordo com o seu sistema operacional. 

* Abra o git bash (se você estiver utilizando Windows) ou o seu terminal e execute o comando abaixo para verificar se o Git foi instalado corretamente em sua máquina: 

```
git --version
```

## 3. Gerando sua chave ssh

* Abra o seu git bash e execute o comando abaixo, substituindo "seu-email-git" para o seu email utilizado ao criar a sua conta do GitHub:

```
ssh-keygen -t rsa -C "seu-email-git"
```

* Inicie o agente SSH com o comando abaixo: 

```
eval "$(ssh-agent -s)"
```

* Com a chave ssh gerada, vamos entrar na pasta onde ela está:

```
cd .ssh/
```

* Vamos listar todos os arquivos e diretórios dentro da pasta .ssh:

```
ls
```

* Pode-se perceber que nesta pasta temos um arquivo chamado id_rsa.pub, vamos ver o conteúdo que tem nele, depois copie ele:

```
cat id_rsa.pub
```

* No GitHub, vá em seu perfil, depois em settings -> SSH and GPG Keys -> New SSH key, dê um título à sua chave ssh e cole-a em Key, conforme print abaixo: 

![chave ssh github](/prints/new_ssh.png)

* Por fim, clique em Add SSH Key.

## 4. Configurar o Git na sua máquina 

* Ainda no git bash, execute os comandos abaixo, substituindo o "username" para o seu nome de usuário(a) e "email" para o seu email utilizado ao criar a conta do GitHub: 

```
git config --global user.name "username"
```

```
git config --global user.email "email" 
```

* Para checar se foi configurado corretamente, basta executar: 

```
git config user.name
```

```
git config user.email
```

## 5. Criando um repositório local

* Aqui vamos utilizar o VS Code como IDE, então instale [VS Code](https://code.visualstudio.com/download) de acordo com o sistema operacional da sua máquina. 

* Abra um novo terminal, conforme print abaixo: 

![terminal do VS Code](/prints/new_terminal.png)

* Crie uma nova pasta: 

```
mkdir repositorios
```

```
cd repositorios
```

```
mkdir projeto-cpbsb6
```

* Feito isso, clique em File e depois em Open Folder, conforme print abaixo, e abra a pasta projeto-cpbsb6: 

![caminho da pasta](/prints/open_folder.png)

* Agora crie um arquivo chamado hello_world.py na sua pasta projeto-cpbsb6.

* Dentro do arquivo, coloque o seguindo comando: 

```
print("Hello, World!")
```

* Salve o arquivo clicando em ctrl + s. 

* Agora vá até o seu terminal e execute o seguinte comando: 

```
git init
```

Esse comando irá transformar a sua pasta em um repositório Git. Você deve visualizar uma mensagem como: Initialized empty Git repository in...

## 6. Conectando o seu repositório local ao seu repositório no GitHub 

* Agora vamos criar um repositório no seu GitHub, vá em Repositories -> New. Dê um nome ao seu repositório e então clique em Create Repository.

* Após criar seu repositório, você verá uma imagem parecida com a imagem abaixo: 

![repo git](/prints/git_init.png)

* No nosso caso, vamos seguir os comandos que estiverem no bloco '…or push an existing repository from the command line'. Então execute os comandos abaixo:

```
git remote add origin https://github.com/<username>/<repository>.git
```

```
git add . 
```

```
git commit -m "feat: criando meu primeiro hello world" 
```

```
git push origin main
```

* Então volte à página do GitHub e atualize-a para verificar as suas mudanças.

* Para mais informações sobre como criar um repositório no GitHub, olhar o [link](https://docs.github.com/pt/repositories/creating-and-managing-repositories/quickstart-for-repositories).

## 7. Entendendo o conceito de branches

* A tradução de branch é a de ramificação. Imagine que em um repositório há uma branch principal (que está em produção), geralmente chamada de 'main'. Mas como você pode fazer testes e desenvolver novos desenvolvimentos de forma isolada sem impactar o que está em produção? Por meio de outras branches! Então você cria outras ramificações para trabalhar nesses novos desenvolvimentos e depois mergeá-los à branch principal.

* Então vamos criar uma nova branch onde iremos fazer uma alteração no nosso arquivo hello_world.py, digite o seguinte comando: 

```
git checkout -b <nome-da-minha-nova-branch>
```

* Como checar se a minha branch foi criada? 

```
git branch
```

* Se você digitar o comando acima, ele mostrará todas as branches deste repositório, a branch que você está é a que começa com *.


## 8. Fork vs Clone

* Clone é uma operação que faz uma cópia de um repositório Git existente para sua máquina local por meio do comando git `git clone <repositorio>`. Com as devidas permissões é possível fazer alterações e subir no repositório remoto. 

* Fork é uma cópia de um repositório Git existente para sua própria conta no GitHub. Com o fork é possível fazer alterações independentes do repositório original. Os forks são muito utilizados na contribuição de projetos com código aberto, onde é feito o fork do projeto, é feito as alterações no repositório 'forkado' e é feito então o 'pull request' para o repositório original com as atualizações. Para que as contribuiçoes sejam 'mergeadas' ou mescladas no repositório orginal passa por uma aprovação dos usuários que tem a devida permissão.


## 9. Staging area

* Staging area ou área de preparação é um conceito intermediário entre o diretório de trabalho e o repositório Git. É onde você prepara as mudanças que deseja incluir no próximo commit. 

* Ao fazer modificações nos arquivos no diretório de trabalho, ao usar o comando `git add` essas mudanças vão para a staging area. Essas alterações estão sendo preparadas para serem incluídas no commit. Ainda na staging area você pode usar o comnado `git reset` e remover as mudanças da staging area.

* Após o `git add` as mudanças passam a estar na staging area. Com o comando `git commit` as mudanças são confirmadas no repositório Git local, não no diretório de trabalho. Isso significa que as alterações agora estão registradas no histórico de commits do seu repositório local. 

* Para que as alterações sejam enviadas para o repositório remoto como o GitHub, é preciso executar o comando `git push`. O `git push` envia os commits locais para o repositório remoto, atualizando o repositório remoto com as mudanças e também as tornam acessíveis para os colaboradores.

![git staging](/prints/git_staging.png)


## 10. Como fazer commit

Após fazer as alterações nos arquivos do diretório de trabalho, é preciso executar o comando `git add` e adicionar os arquivos modificados, por exemplo:

```
git add <arquivo1> <arquivo2> <arquivo3>
```

onde `<arquivo1>` é o nome de cada arquivo alterado. É possível ver cada arquivo quando executar o comando `git status`.

Sabendo que as alterações estão na staging area, para que as alterações sejam incluídas no repositório é preciso executar o comando `git commit`. Assim como ao salvar um arquivo que foi editado, um commit registra alterações em um ou mais arquivos no seu branch. O Git atribui a cada commit um ID exclusivo, denominado SHA ou hash, que identifica:

- Cada uma das alterações feitas;
- O momento em que as alterações foram feitas;
- O autor das alterações.

Ao fazer um commit, você deve incluir uma mensagem que descreva brevemente as alterações com o seguinte comando:

`git commit -m "mensagem de commit"`

Sites de apoio ao material: 

<https://docs.github.com/pt/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/about-commits>

<https://petcomputacaoufrgs.github.io/intro-ao-git/>


## 11. Outros comandos

### git status

O comando `git status` mostra o estado do diretório de trabalho e da staging area. Ao executar o comando, o Git fornece informações sobre quais arquivos foram modificados, adicionados ou removidos desde o último commit, e também informa sobre arquivos que estão na staging area, prontos para serem commitados.

Para executar o comando:

`git status`


### git log

O comando `git log` permite visualizar o histórico do repositório. Sua forma mais básica é:

`git log`

É possível compactar a formatação do comando:

`git log --oneline`

### git show

Com o comnado `git show` é  utilizado para exibir informações detalhadas sobre um commit específico. Quando você executa git show seguido do identificador do commit (geralmente um hash SHA), o Git exibe informações sobre esse commit.

O git show também pode ser utilizado sem especificar um commit, neste caso, ele exibirá as informações do commit mais recente.

`git show`

### git diff

Para visualizar diferenças entre versões do projeto, é possível utilizar o comando git diff. O comando exibe diferenças no seguinte formato: uma versão é dada como versão mais antiga, a outra como mais nova, as linhas que a versão mais nova introduziu são marcadas com um + e as que a versão mais nova removeu são marcadas com um -. Para visualizar a diferença entre um commit antigo "hash_commit_antigo" e um commit novo "hash_commit_novo", basta executar:

`git diff hash_commit_antigo hash_commit_novo`

Para sair do comando, basta digitar `q`.

Para comparar duas branches `main` e `dev`, basta executar:


`git diff main dev`

### git clone

O comando `git clone` é usado para criar uma cópia local de um repositório Git remoto. Geralmente é usado quando deseja iniciar o desenvolvimento em um novo projeto, colaborar em um projeto existente ou criar uma cópia de backup de um repositório remoto.


`git clone <link-repo>`