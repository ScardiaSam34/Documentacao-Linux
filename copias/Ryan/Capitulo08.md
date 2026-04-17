# Capítulo 8 – Finding Linux Documentation

## Tópicos
- Introdução
- Fontes de documentação no Linux
- Manual pages (man)
- Sistema de documentação GNU Info
- Opção --help e comando help
- Outras fontes de documentação
- Processos no Linux
- Gerenciamento de processos
- Monitoramento de processos
- Agendamento de tarefas

---

## Subtópicos

### Introdução
Este capítulo apresenta as principais formas de encontrar documentação e ajuda dentro do sistema Linux. Como o Linux possui uma grande quantidade de ferramentas e comandos, é essencial saber onde buscar informações quando surgirem dúvidas.

O sistema oferece várias fontes de documentação integradas, além de muitos recursos disponíveis online.

Além disso, o capítulo também aborda **conceitos importantes sobre processos no Linux**, incluindo como eles funcionam, como monitorá-los e como agendar tarefas no sistema.

---

### Fontes de documentação no Linux
Existem diversas formas de acessar documentação no Linux. As principais incluem:

- man pages
- GNU Info System
- opções de ajuda dos comandos
- documentação instalada com pacotes
- sistemas de ajuda gráficos
- documentação online

Essas ferramentas permitem consultar informações sobre comandos, arquivos de configuração, bibliotecas e outros componentes do sistema.

---

### Manual pages (man)

#### The man pages
As **man pages** são uma das principais fontes de documentação no Linux. Elas fornecem informações detalhadas sobre comandos, programas, arquivos de configuração e componentes do sistema.

Cada programa normalmente possui sua própria página de manual, que explica como ele funciona e quais opções podem ser utilizadas.

---

#### O comando man
O comando **man** é utilizado para acessar as páginas de manual do sistema. Ele pesquisa, formata e exibe a documentação disponível.

Exemplo:

```
man ls
man passwd
```

Esse comando abre a página de manual do comando ls.

Também é possível buscar por palavras-chave nas descrições das man pages usando a opção -k (que funciona de forma idêntica ao comando apropos):

```
man -k "copy files"
apropos "directory"
```

---

#### Manual Chapters
As man pages são organizadas em diferentes seções chamadas **chapters** (ou seções), que classificam o tipo de conteúdo da documentação.

Algumas seções comuns incluem:

1 – comandos de usuário  
2 – chamadas do sistema  
3 – funções de bibliotecas  
4 – arquivos de dispositivos  
5 – formatos de arquivos e arquivos de configuração  
6 – jogos  
7 – informações diversas  
8 – comandos administrativos do sistema  

Essa organização facilita encontrar documentação específica para diferentes partes do sistema. Para acessar uma seção específica, basta digitar o número antes do comando:

```
man 1 passwd
man 5 passwd
```

---

#### Usando o man
Ao abrir uma man page, é possível navegar pelo conteúdo utilizando comandos do teclado. As páginas normalmente incluem:

- descrição do comando
- sintaxe
- opções disponíveis
- exemplos de uso
- arquivos relacionados

Para navegar dentro de uma man page, utilize as seguintes teclas:

```
Seta para baixo / Seta para cima -> Rola linha por linha
Space -> Avança uma página
b -> Volta uma página
/palavra -> Pesquisa por "palavra" no documento
n -> Próximo resultado da pesquisa
q -> Sai do manual
```

---

### GNU Info

#### O sistema GNU Info
O **GNU Info System** foi criado pelo projeto GNU como um sistema de documentação mais estruturado que as man pages.

Ele permite navegar por documentos organizados em uma estrutura semelhante a um menu ou árvore de navegação.

---

#### Usando info na linha de comando
A documentação do sistema Info pode ser acessada através do comando:

```
info
info ls
```

Esse comando abre o sistema de documentação Info no terminal.

---

#### Estrutura das páginas info
As páginas do Info são organizadas em **nós (nodes)** conectados entre si, permitindo navegar entre diferentes partes da documentação.

---

#### Navegação no Info
Teclas comuns de navegação:

```
Enter -> Entra no link selecionado
n -> Próxima página
p -> Página anterior
u -> Sobe um nível
q -> Sai do sistema info
```

---

### A opção --help e o comando help

#### A opção --help
Muitos comandos Linux oferecem uma opção de ajuda rápida utilizando o argumento `--help`.

Exemplo:

```
ls --help
mkdir --help
```

Essa opção mostra um resumo das opções disponíveis.

---

#### O comando help
O comando **help** é usado principalmente para obter ajuda sobre comandos internos do shell.

Exemplo:

```
help cd
help echo
```

---

### Outras fontes de documentação

#### Sistemas de ajuda gráfica
Ambientes gráficos como GNOME ou KDE oferecem sistemas de ajuda integrados que permitem consultar documentação através de interfaces visuais.

---

#### Documentação de pacotes
Muitos programas incluem documentação adicional instalada no sistema, normalmente localizada em:

```
/usr/share/doc/
```

Esses diretórios podem conter arquivos como README, exemplos e guias de uso.

---

#### Recursos online
Além da documentação local, também existem muitos recursos disponíveis online, como:

- documentação oficial
- fóruns da comunidade
- wikis
- tutoriais técnicos
- guias de administração

---

# Processos no Linux

### O que é um processo
Um **processo** é uma instância de um programa em execução no sistema.

Quando um programa é executado, o sistema cria um processo para gerenciar sua execução.

Cada processo possui informações como:

- identificador único
- prioridade
- estado atual
- recursos utilizados

---

### Identificação de processos

Cada processo possui um identificador único chamado **PID (Process ID)**.

Além disso, processos podem ter um **PPID (Parent Process ID)**, que indica qual processo criou aquele processo.

---

### Tipos de processos

Alguns tipos comuns incluem:

**Interactive processes**  
São iniciados pelo usuário através do terminal.

**Batch processes**  
São executados automaticamente em segundo plano sem interação direta com o usuário.

**Daemons**  
São processos que executam em segundo plano e normalmente iniciam durante a inicialização do sistema.  
Eles aguardam requisições do sistema ou dos usuários.

---

### Estados de processos

Durante sua execução, um processo pode estar em diferentes estados:

- **Running** → processo em execução  
- **Sleeping (Waiting)** → aguardando algum evento ou recurso  

---

### Prioridade de processos (nice)

No Linux, processos possuem prioridades que determinam quanto tempo de CPU recebem.

O valor **nice** controla essa prioridade.

Regras importantes:

- **valores menores de nice → maior prioridade**
- **valores maiores de nice → menor prioridade**

---

### Controle de processos no terminal

Quando um processo está sendo executado no terminal, é possível controlá-lo utilizando atalhos do teclado.

**Encerrar processo em primeiro plano**

```
CTRL + C
```

Esse atalho termina imediatamente o processo atual.

---

**Suspender processo**

```
CTRL + Z
```

Esse comando suspende o processo atual.

---

### Processos em foreground e background

Um processo pode ser executado em:

**Foreground**  
Executa diretamente no terminal e bloqueia o prompt.

**Background**  
Executa em segundo plano permitindo continuar utilizando o terminal.

---

### Comandos para controle de processos

**Trazer processo para foreground**

```
fg
```

---

**Colocar processo em background**

```
bg
```

---

**Listar processos em background da sessão**

```
jobs
```

---

# Monitoramento de processos

### Visualizando processos

Alguns comandos importantes para visualizar processos incluem:

```
top
pstree
```

---

### Comando top

O **top** mostra processos em tempo real e informações como:

- PID
- usuário (USER)
- prioridade (PR)
- uso de CPU
- uso de memória

Também mostra informações gerais do sistema como:

- processos ativos
- processos parados
- processos zombie

---

#### Ordenação no top

Durante o uso do top, é possível ordenar processos por consumo de recursos pressionando:

```
A
```

---

### Comando pstree

O comando **pstree** mostra os processos em forma de árvore.

Ele permite visualizar:

- relação entre processos **pai e filho**
- **threads**, exibidas entre chaves `{}`

---

# Agendamento de tarefas

### Cron

O **cron** é um serviço utilizado para executar tarefas automaticamente em intervalos regulares.

Ele é usado para tarefas como:

- backups automáticos
- execução de scripts
- manutenção do sistema

---

### at

O comando **at** permite executar um programa **uma única vez em um horário específico**.

Ele é utilizado para executar programas **não interativos** no futuro.

---

## Conteúdo

Neste capítulo aprendi como encontrar documentação dentro do sistema Linux utilizando ferramentas integradas como **man**, **info**, **--help** e **help**. Essas ferramentas permitem consultar rapidamente informações sobre comandos e programas instalados no sistema.

Também aprendi que existem outras fontes de documentação, como arquivos instalados com pacotes, sistemas de ajuda gráfica e diversos recursos disponíveis online.

Além disso, entendi conceitos importantes sobre **processos no Linux**, incluindo como eles são identificados através do **PID**, quais estados podem possuir e como sua prioridade pode ser controlada através do valor **nice**.

Aprendi também como **controlar processos pelo terminal**, utilizando atalhos como **CTRL+C** para terminar um processo e **CTRL+Z** para suspender sua execução.

Outro ponto importante foi o **monitoramento de processos**, utilizando comandos como **top** e **pstree**, que permitem visualizar informações sobre processos em execução.

Por fim, conheci ferramentas de **agendamento de tarefas**, como **cron**, que permite executar tarefas periodicamente, e **at**, que permite agendar a execução de programas em um horário específico.

Esses recursos são fundamentais para administrar sistemas Linux e entender como o sistema gerencia programas em execução.

---

# Comandos do Capítulo

| Comando | Descrição |
|--------|-----------|
| man | Abre a página de manual de um comando |
| apropos | Busca comandos por palavra-chave |
| info | Abre documentação no formato Info |
| help | Mostra ajuda para comandos internos do shell |
| top | Mostra processos em execução em tempo real |
| pstree | Mostra processos em forma de árvore |
| fg | Traz processo para foreground |
| bg | Coloca processo suspenso em background |
| jobs | Lista processos da sessão atual |
| cron | Executa tarefas programadas |
| at | Agenda execução única de um comando |

---

## Recursos úteis
https://linuxcommand.org  
https://tldp.org  
https://kernel.org