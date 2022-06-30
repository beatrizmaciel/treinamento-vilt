# TREINAMENTO VILT
Este treinamento de Git foi feito para o evento da FIEC em parceria com a Vilt. O intuito é aprender comandos básicos de versionamento de código, utilizados no dia a dia de um(a) programador(a).


# Git

É um sistema de versionamento de controle para rastrear mudanças em arquivos do computador coordenando o trabalho feito nestes arquivos entre uma ou múltiplas pessoas.

### Download

Baixar o Git é fácil! Basta entrar em [git-scm.com](https://git-scm.com/downloads), baixar a última versão e seguir os passos para a instalação. Bem intuitivo.

### Configuração

A primeira coisa que devemos fazer é configurar nosso git. Se você tem dúvidas, use o seguinte comando:

```bat
git help
```

Usando esse comando você encontra uma série de utilizações do git. Para começar, vamos colocar nosso nome de usuário (o que vai aparecer quando publicarmos uma versão de código) e nosso e-mail, que ajuda na identificação e nas permissões.

```bat
git config --global user.name "Nina Silva"
```

```bat
git config --global user.email "nina@learning-git.com"
```

Nesse caso usamos "--global" para que a identificação seja global (em todo o sistema), mas podemos também definir identificações para repositórios específicos, substituindo o --global por --local, dessa forma:

```bat
git config --local user.name "Grace Hooper"
```

### Comandos

#### :pencil2: Inicializando um repositório

```bat
git init
```
Para inicializar do zero.

```bat
git clone
```
Para clonar algum repositório. É preciso especificar qual repositório será clonado depois da palavra "clone"

#### :pencil2: Puxando atualizações de um repositório

Muitas vezes, quando estamos compartilhando código com outras pessoas, é importante "puxar" todas as atualizações feitas remotamente para o nosso local. Para isso utilizamos o seguinte comando:

```bat
git pull
```

Pull em inglês é "puxar", não se confunda! :wink:

#### :pencil2: Fazendo atualizações

Agora chegou a hora de entregarmos nossas modificações para o repositório remoto. Geralmente quando trabalhamos em equipe trabalhamos em branches, que significa ramos ou ramificações. Geralmente um repositório tem um branch master, que concentra todo o código que já foi revisado e está correto, enquanto os desenvolvedores trabalham em branches separadamente.
Quando fazemos um clone de um repositório e atualizamos ele (pull), ficamos geralmente na branch master. Para fazermos uma ramificação, que será nosso ambiente de trabalho, usamos o seguinte comando:

```bat
git checkout -b minha-branch
```

O `git checkout` serve para sairmos de uma branch e entrarmos em outra, mas quando utilizamos o comando `-b` criamos uma nova branch! Nesse caso o nome da branch é "minha-branch", mas poderia ser "bananinha", "componente-banner" ou qualquer outra coisa.

:heavy_exclamation_mark: Importante! Usamos um padrão para criarmos novas branches. Geralmente usamos `feature/` , `bug/` ou `hotfix/` antes do nome da nossa branch e esses acordos precisam ser feitos a priori com o time. Cada equipe se organiza de uma forma diferente, mas tenha em mente que quando criamos um novo componente ou versão usamos `feature/minha-branch`. Se estamos consertando um bug, `bug/minha-branch` e se é um hot fix, ou seja, uma melhoria urgente, usamos `hotfix/minha-branch`.

Depois de criarmos nossa branch vamos fazer as modificações necessárias em casa arquivo. Uma vez que terminamos de fazer as atualizações podemos adicionar nossa nova versão de código na nossa branch. Para isso, abrimos o terminal git bash e conferimos quais arquivos foram modificados com o seguinte comando:

```bat
git status
```

O git status nos ajuda a ver arquivos que foram mapeados pelo git. Nesse caso vamos adicioná-los usando o seguinte comando:

```bat
git add "nome do arquivo"
```

Ao usarmos o git status depois de adicionar um arquivo, vemos que sua cor muda de vermelho para verde e isso significa que as mudanças estão prontas para serem atualizadas. Para criar uma versão desse arquivo usamos o comando:

```bat
git commit -m "escreva uma mensagem aqui"
```

É importante escrevermos uma mensagem descrevendo o que fizemos na alteração do código. Precisamos ser sucintos e objetivos, porque se for preciso um dia voltar a esse commit sabemos exatamente o que foi feito. Exemplos de mensagens de commits: "criando os estilos do componente", "atualizando o serviço de mensageria", "adicionando versão mobile", "passando testes unitários" e por aí vai.
Uma coisa muito legal de usar nas mensagens de commits é o [gitmoji.dev](https://gitmoji.dev/)! Ele deixa os commits mais visuais!

Depois de ter feito o commit das suas modificações (não economize nos commits! Faça sempre que achar necessário) é preciso "empurrar" essas modificações para a sua branch (sim, ainda estamos trabalhando na nossa branch: minha-branch). Para isso usamos o seguinte comando:

```bat
git push origin minha-branch
```

É importante usarmos o origin antes da nossa branch, porque algumas vezes vamos trabalhar com branches de mesmo nome, sendo uma em cloud e outra a origin. É bom se acostumar a sempre especificar qual branch você quer puxar ou empurrar conteúdos.

#### :pencil2: Conferindo as mudanças

Pronto! Agora suas atualizações podem ser acessados por qualquer desenvolvedor. Para verificarmos se o nosso commit foi realmente efetuado usamos o seguinte comando:

```bat
git log
```

O git log nos ajuda a ver todo o histórico de commits da branch, desde o seu "nascimento" na master. Também podemos ver os commits em outras plataformas, como Github, o Gitlab e o Bitbucket, mas quando não tivermos essas plataformas para nos ajudarmos é bom usar o git log e conferir se está tudo certinho.

#### :pencil2: Mesclando branches

Trabalho concluído e agora é hora de fazer o merge da sua branch na branch master! O merge é quando mesclamos uma branch na outra, levando todas as nossas atualizações para outra branch.

:heavy_exclamation_mark: Importante! Fazer o merge com outra branch pode ser um pouco complicado nas primeiras vezes, então é importante avisar os colegas que você fará esse movimento. Muitas vezes também precisamos resolver conflitos entre a nossa branch e a branch master (ou qualquer outra branch que vamos mesclar). É preciso ficar atento para não deixar bugs e erros passarem nesse momento. Faça tudo com orientação das primeiras vezes

Vamos pensar numa situação imaginária: pense que você quer levar todas as atualizações da minha-branch para a branch master. Para fazer isso nós vamos fazer `git checkout master`, onde vamos mudar para a branch master. Depois disso, rodaremos o seguinte comando:

```bat
git merge minha-branch
```

Dessa forma estaremos mesclando a nossa branch (minha-branch) dentro da branch master e teremos todas as atualizações!

#### :pencil2: Salvando alterações sem fazer commit

Agora que já entendemos o que são commits e sabemos que temos um histórico deles quando rodamos o comando `git log`, surge uma nova dúvida: o que fazer quando estamos trabalhando em uma atualização, mas ainda não terminamos e precisamos resolver algo em outra branch rapidamente? Se você já foi interrompido(a) fazendo alterações em uma branch sabe que o git não permite que mudemos de uma branch para outro com atualização "a commitar", ou seja, pendentes.
Para que nós não perdamos essas modificações, podemos usar o seguinte comando:

```
git stash
```

O git stash serve para salvarmos em uma fração da memória do computador nossas alterações sem commitar elas. Esse comando é bem útil quando estamos escrevendo algo que ainda não traz nenhum benefício para o nosso código, mas não queremos perder o que começamos. Para aplicar o que estava em stash usamos o comando `git stash apply`. Também é possível listar quantos stashs foram feitos através do `git stash list` ou limpar os stashs com `git stash clear`.