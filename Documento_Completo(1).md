# INTRODUÇÃO AO LINUX
![Linux](https://img.shields.io/badge/Linux-000000.svg?style=for-the-badge&logo=linux&logoColor=white)

## Tópicos
- 1. [História e Conceitos Fundamentais](#1-história-e-conceitos-fundamentais)
- 2. [Distribuições e Inicialização](#2-distribuições-e-inicialização)
- 3. [Interface Gráfica](#3-interface-gráfica)
    - 3.1 [Aplicações na Internet e Produtividade](#31-aplicações-na-internet-e-produtividade)
- 4. [Linhas de Comando](#4-linhas-de-comando)
    - 4.1 [Documentação Linux](#41-documentação-linux)
    - 4.2 [Processos](#42-processos)
- 5. [Operações com Arquivos](#5-operações-com-arquivos)
- 6. [Editores de Texto](#6-editores-de-texto)
    - 6.1 [Ambiente do Usuário](#61-ambiente-do-usuário)
    - 6.2 [Manipulação de Texto](#62-manipulação-de-texto)
- 7. [Operações com Conexões de Rede](#7-operações-com-conexões-de-rede)
- 8. [Bash e Scripting](#8-bash-e-scripting)
    - 8.1 [Shell Script Avançado](#81-shell-script-avançado)
- 9. [Segurança e Impressão](#9-segurança-e-impressão)

***

# 1. História e Conceitos Fundamentais

A **Linux Foundation** atua como uma organização "guarda-chuva" para projetos de código aberto (Open Source) vitais para a infraestrutura tecnológica global, como Kubernetes e Node.js. Sua missão é fornecer expertise para iniciativas que resolvem problemas complexos por meio de colaboração open source, com um modelo de ensino "para a comunidade e pela comunidade".

O Linux foi criado por Linus Torvalds em 1991 e é fortemente inspirado no UNIX. Uma característica central de sua filosofia é que quase tudo no sistema é tratado como arquivo ou objeto. O sistema é completamente multi-tarefa e multi-usuário, suportando vários processos e usuários simultâneos sem perda de performance. O kernel é licenciado sob a GPL v2 (GNU General Public License), garantindo que o código-fonte seja aberto e redistribuível.

**Terminologia Essencial:**
* **Kernel:** O núcleo do sistema operacional, responsável por gerenciar o hardware e a memória.
* **Distribuição:** O pacote completo que une o kernel a ferramentas essenciais, gerenciadores de pacotes e ambientes de desktop.
* **Daemons:** Processos de serviços de rede que rodam silenciosamente em segundo plano.

***

# 2. Distribuições e Inicialização

As distribuições Linux se organizam em três grandes famílias:

| Família | Distribuições Representantes | Gerenciador de Pacotes | Foco Principal |
| :--- | :--- | :--- | :--- |
| **Red Hat** | RHEL, CentOS, Fedora, Oracle Linux | `yum` / `dnf` / `rpm` | Corporativo e Servidores |
| **SUSE** | SUSE Linux Enterprise, openSUSE | `zypper` / `rpm` | Inovação e Varejo |
| **Debian** | Debian, Ubuntu, Linux Mint | `apt` / `apt-get` / `dpkg` | Estabilidade, Desktop e Cloud |

### Processo de Inicialização (Boot)
A inicialização de um sistema Linux moderno segue um fluxo bem definido:
1. **BIOS / UEFI:** Executa o POST (Power-On Self Test) e localiza o setor do bootloader.
2. **Boot Loader (GRUB2):** Carrega o kernel na memória RAM e permite escolher entre múltiplos sistemas.
3. **Kernel:** Descomprime os dados, detecta o hardware e monta o sistema de arquivos raiz (`/`).
4. **initramfs:** Monta um sistema de arquivos temporário em RAM, essencial para o boot.
5. **systemd (PID 1):** Substituto do antigo SysVinit. É o "pai" de todos os processos, gerenciando serviços e inicializando o sistema em paralelo para maior velocidade.

***

# 3. Interface Gráfica

O sistema gráfico base do Linux usa tradicionalmente o **X Window System (X11)**, mas sistemas mais modernos adotam o protocolo **Wayland** (padrão em distros como Fedora e RHEL 8+).

O **Gerenciador de Exibição (Display Manager)**, como o GDM (GNOME Display Manager), é responsável por gerenciar a tela de login e iniciar o ambiente após a autenticação.

**Ambientes de Desktop (DE) Populares:**
* **GNOME:** Padrão no Ubuntu e Fedora, com foco em simplicidade.
* **KDE Plasma:** Altamente customizável, ideal para usuários habituados ao Windows.
* **XFCE / LXDE:** Ambientes leves focados em performance, ideais para hardwares mais antigos.

As configurações gerais do sistema — como resolução de tela, duplo monitor e data/hora — podem ser feitas pelo painel de Configurações. O sistema usa internamente o padrão **UTC** e sincroniza o horário pela internet via protocolo **NTP (Network Time Protocol)**. O **Network Manager** gerencia Wi-Fi, dados móveis e conexões VPN.

## 3.1 Aplicações na Internet e Produtividade

O ecossistema Linux oferece programas equivalentes para as principais demandas do cotidiano e do desenvolvimento:

| Categoria | Softwares e Ferramentas | Descrição |
| :--- | :--- | :--- |
| **Navegadores** | Firefox, Chrome, w3m, lynx | w3m e lynx rodam inteiramente via terminal, em modo texto. |
| **Produtividade** | LibreOffice (Writer, Calc, Impress) | Suíte de escritório completa com compatibilidade aos formatos do MS Office. |
| **Multimídia** | VLC, Rhythmbox, Audacity | Ferramentas robustas para reprodução e edição de áudio e vídeo. |
| **Design Gráfico**| GIMP, Inkscape, Blender | GIMP é a principal alternativa ao Photoshop para edição avançada de imagens. |

***

# 4. Linhas de Comando

> *"A interface gráfica torna tarefas fáceis ainda mais fáceis, enquanto as linhas de comando tornam tarefas difíceis possíveis."*

A interface de linha de comando (CLI), onde o **bash** (Bourne Again Shell) é o shell mais comum, oferece controle completo sobre o sistema. O acesso pode ser feito via Terminais Virtuais (TTY, com `Ctrl+Alt+F2` a `F6`) ou por emuladores de terminal nas interfaces gráficas.

**Características Principais:**
* Toda e qualquer tarefa do sistema pode ser realizada via linha de comando.
* É possível criar scripts para automatizar sequências de comandos repetitivos ou complexos.
* Aplicações gráficas podem ser iniciadas pelo terminal, sem precisar navegar entre menus e janelas.
* Os comandos são padronizados, inclusive entre diferentes distribuições.

**Elementos de um Comando:**
* **Comando:** a instrução principal a ser executada.
* **Opções (flags):** modificam o comportamento do comando; começam com `-` ou `--` para se diferenciarem dos argumentos.
* **Argumentos:** os alvos ou parâmetros sobre os quais o comando age.

**Caminhos (Paths) de Navegação:**
* **Caminho Absoluto:** Parte sempre da raiz `/` (ex: `/etc/passwd`).
* **Caminho Relativo:** Depende do diretório de trabalho atual do usuário.

### Fluxo Padrão de Arquivos

Todo processo no Linux opera com três fluxos de dados padrão:
* **stdin** (standard input) → entrada de dados.
* **stdout** (standard output) → saída dos resultados.
* **stderr** (standard errors) → saída de mensagens de erro.

### Redirecionamento de E/S (Entrada/Saída)

O shell permite usar os símbolos `>` e `<` para redirecionar esses fluxos:

| Símbolo | Função |
| :--- | :--- |
| `>` | Redireciona a saída para um arquivo, sobrescrevendo seu conteúdo |
| `<` | Usa um arquivo como entrada para um comando |
| `2>` | Redireciona mensagens de erro para um arquivo |
| `2>&1` ou `>&` | Redireciona tanto a saída quanto os erros para o mesmo arquivo |

### Caracteres Coringas (Wildcards)

Utilizados para criar padrões de busca e seleção de arquivos:

| Caractere | Função |
| :--- | :--- |
| `?` | Substitui exatamente um único caractere |
| `*` | Substitui qualquer sequência de caracteres (palavra ou string) |
| `[conjunto]` | Corresponde a qualquer caractere dentro do conjunto especificado |
| `[!conjunto]` | Corresponde a qualquer caractere **fora** do conjunto especificado |

### Links 

#### Hard Links
São arquivos independentes que compartilham a mesma partição de dados de outro arquivo no mesmo disco.

>  **Atenção:** Se um dos arquivos for excluído, o outro permanece — mas se um for editado de forma incompatível, o link pode ser quebrado ou os arquivos podem se sobrescrever.

#### Soft Links (Links Simbólicos)
Ao contrário dos hard links, não ocupam espaço de dados no disco. Funcionam como atalhos que apontam para outro arquivo, de forma similar aos atalhos da área de trabalho do Windows.

* Criação de hard link: `ln arquivo_origem link_destino`
* Criação de soft link: `ln -s arquivo_origem link_destino`

### Comandos de Navegação e Diretórios

| Comando | Descrição |
| :--- | :--- |
| `pwd` | Exibe o diretório de trabalho atual |
| `cd ~` | Retorna ao diretório home do usuário |
| `cd ..` | Sobe para o diretório pai |
| `cd -` | Volta ao último diretório acessado |
| `cd /` | Vai para o diretório raiz |
| `ls` | Lista o conteúdo do diretório atual |
| `ls -a` | Lista todo o conteúdo, incluindo arquivos ocultos |
| `ls -la` | Lista detalhadamente, incluindo permissões e arquivos ocultos |
| `pushd` | Muda de diretório e salva o atual na pilha |
| `popd` | Retorna ao diretório anterior da pilha |
| `dirs` | Exibe a pilha de diretórios visitados |
| `tree` | Exibe a árvore de diretórios a partir do local atual |

### Comandos de Criação e Manipulação de Arquivos

| Comando | Descrição |
| :--- | :--- |
| `touch nome` | Cria um novo arquivo vazio |
| `touch -a nome` | Atualiza o timestamp do arquivo para o momento atual |
| `touch -r ref dest` | Copia os metadados de timestamp do arquivo de referência para o destino |
| `touch nome{1..3}` | Cria múltiplos arquivos de uma vez (ex: `nome1`, `nome2`, `nome3`) |
| `mkdir nome` | Cria um novo diretório |
| `mkdir /caminho/` | Cria um diretório no caminho especificado |
| `mv antes depois` | Renomeia um arquivo |
| `mv nome /caminho/` | Move um arquivo para o caminho desejado |
| `rm nome` | Remove um arquivo |
| `rm -f nome` | Remove um arquivo de forma forçada |
| `rm -i nome` | Remove com confirmação interativa |
| `rm -rf nome` | Remove um diretório e todos os seus conteúdos recursivamente |
| `rmdir nome` | Remove um diretório vazio |
| `cat` | Cria, concatena e exibe o conteúdo de arquivos |
| `echo` | Exibe texto ou manipula saídas formatadas no terminal |

### Comandos de Visualização de Arquivos

| Comando | Descrição |
| :--- | :--- |
| `less arquivo` | Exibe o arquivo de forma paginada e navegável |
| `tac arquivo` | Exibe o conteúdo do arquivo em ordem inversa |
| `tail -n arquivo` | Exibe as últimas `n` linhas do arquivo |
| `head -n arquivo` | Exibe as primeiras `n` linhas do arquivo |

### Comandos de Busca e Localização

| Comando | Descrição |
| :--- | :--- |
| `which programa` | Localiza o caminho do executável de um programa |
| `whereis programa` | Localiza o executável, as páginas de manual e os arquivos fonte de um programa |
| `locate padrão` | Busca rápida por arquivos usando banco de dados indexado |
| `locate zip \| grep bin` | Exemplo: filtra resultados com `zip` e `bin` no caminho |
| `find` | Lista todos os arquivos no diretório atual e subdiretórios |
| `find -name padrão` | Busca arquivos pelo nome com distinção entre maiúsculas e minúsculas |
| `find -iname padrão` | Busca arquivos pelo nome ignorando maiúsculas/minúsculas |
| `find -d` | Restringe a busca apenas a diretórios |
| `find -f` | Restringe a busca apenas a arquivos comuns |
| `find -l` | Restringe a busca apenas a soft links |

### Comandos Gerais do Shell

| Comando | Descrição |
| :--- | :--- |
| `man comando` | Acessa o manual de um comando, função ou programa |
| `exit` | Encerra a sessão atual do shell |
| `login` | Inicia um novo login no shell |

## 4.1 Documentação Linux

A documentação no Linux é vasta, cobrindo comandos, serviços e o próprio kernel:
1. **`man` (Manual Pages):** Referência clássica offline (`man ls`). É dividido em seções: seção 1 para comandos de usuário, seção 5 para formatos de arquivo (ex: `man 5 passwd`) e seção 8 para comandos de administração.
2. **`info`:** Sistema de documentação do GNU estruturado em nós interligados como hiperlinks.
3. **`--help` / `help`:** `ls --help` gera um resumo rápido na tela. O comando `help` é destinado exclusivamente a comandos internos (built-ins) do shell, como `cd` ou `alias`.

## 4.2 Processos

Um processo é uma instância de um programa em execução. Cada processo recebe um **PID** (Process ID) único no sistema. O Linux classifica os processos como interativos ou daemons (segundo plano).

**Monitoramento e Controle:**
* `ps aux` ou `ps -ef`: Captura um instantâneo de todos os processos em execução.
* `top` / `htop`: Exibe um monitor dinâmico em tempo real com uso de CPU, memória e carga média do sistema (Load Average).
* **Niceness (Prioridade):** Controla o tempo de processador alocado a uma tarefa. Varia de -20 (prioridade máxima) até +19 (prioridade mínima).
* **Controle:** `kill <PID>` encerra um processo; `kill -9 <PID>` força o encerramento. `Ctrl+C` interrompe processos em primeiro plano e `Ctrl+Z` os suspende.

**Agendamento de Tarefas:**
* `at`: Agenda um comando ou script para execução única em horário futuro.
* `cron`: Usado via `crontab -e` para tarefas repetitivas, configuráveis por minuto, hora, dia e mês.

***

# 5. Operações com Arquivos

No Linux, a estrutura é regida pelo **FHS (Filesystem Hierarchy Standard)**, partindo do diretório raiz `/`. Quase tudo no sistema, incluindo dispositivos de hardware, é tratado como arquivo.

**Hierarquia Principal:**
* `/bin` e `/sbin`: Binários essenciais para usuário comum e administração, respectivamente.
* `/etc`: Armazena os arquivos de configuração globais do sistema.
* `/var`: Dados variáveis, como logs, filas de e-mail e spool de impressão.
* `/dev`: Arquivos especiais e nós de dispositivos do sistema.
* `/proc` e `/sys`: Sistemas de arquivos virtuais gerados em RAM em tempo real, com informações sobre o kernel e processos ativos.
* `/home` e `/root`: `/home` guarda os perfis dos usuários regulares; `/root` é exclusivo do superusuário.

**Montagem e Operações:**
* **`mount` / `umount`:** O Linux não usa letras de unidade (como C:); as partições são montadas em diretórios. O arquivo `/etc/fstab` define as montagens automáticas no boot.
* **Manipulação Geral:** `cp` para copiar, `mv` para mover e `rm` para remover. O `rsync` é preferível para backups por copiar apenas os blocos modificados (deltas).
* **Cópia de Baixo Nível:** O `dd` faz clones bit a bit de partições inteiras e imagens ISO.

| Comando | Descrição |
| :--- | :--- |
| `df -h` | Mostra o espaço total usado e livre nos discos (formato legível) |
| `du -sh /pasta` | Resume o espaço consumido por um diretório específico |
| `tar -czvf` | Agrupa e compacta diretórios com `tar` + `gzip` |
| `find / -name` | Pesquisa arquivos em toda a hierarquia de diretórios |
| `locate` | Busca rápida por arquivos usando banco de dados indexado |
| `file` | Verifica o tipo real de um arquivo, ignorando sua extensão |

***

# 6. Editores de Texto

Editar arquivos de configuração é uma tarefa rotineira para administradores Linux. As principais opções disponíveis são:

1. **nano:** O editor mais simples no terminal. Não exige memorização — todos os atalhos principais (`Ctrl+O` para salvar, `Ctrl+X` para sair) ficam visíveis permanentemente no rodapé.
2. **gedit:** Editor padrão do GNOME, amigável e com suporte a abas.
3. **vi / vim:** Presente em praticamente todos os servidores UNIX e Linux. Possui curva de aprendizado íngreme por trabalhar em três modos: **Normal** (navegação e edição estrutural), **Inserção** (digitação de texto) e **Comando** (salvar com `:w` ou sair com `:q`). Use `vimtutor` para aprender de forma interativa.
4. **Emacs:** Editor avançado e extensível, com atalhos complexos usando `Ctrl` e `Alt`. Pode funcionar como um ecossistema completo de desenvolvimento.

## 6.1 Ambiente do Usuário

O Linux isola perfeitamente os arquivos de múltiplos usuários simultâneos. O usuário **root (UID 0)** possui privilégios totais. Recomenda-se usar **`sudo`** em vez de `su`, pois o `sudo` registra auditoria das ações e exige apenas a senha do próprio usuário, preservando a senha do administrador.

* **Arquivos do Shell:** `/etc/profile` define variáveis globais para todos os usuários, enquanto `~/.bashrc` configura aliases, cores do prompt e regras locais de cada usuário.
* **Variáveis de Ambiente:** Armazenam informações em memória (listáveis com `env`), como `$HOME`, `$PATH` (diretórios de busca de executáveis) e `$PS1` (formato do prompt).
* **Permissões (chmod):** O acesso é dividido entre dono, grupo e outros (u, g, o). O formato octal `chmod 755` significa: dono pode Ler(4)+Escrever(2)+Executar(1); demais usuários podem Ler(4)+Executar(1). Use `chown` para alterar o proprietário e `chgrp` para alterar o grupo de um arquivo.

## 6.2 Manipulação de Texto

Utilitários que, combinados, permitem transformar e extrair informações de grandes volumes de texto:

* **Visualizar:** `cat` (exibe o arquivo completo), `tac` (exibe em ordem inversa), `less` (navegação interativa em arquivos longos), `head` e `tail` (primeiras ou últimas linhas).
* **Filtrar:** `grep` pesquisa palavras e padrões regulares dentro de textos — essencial para investigar arquivos de log.
* **Extrair e Formatar:** `sed` atua como editor de fluxo para substituições em massa (`sed 's/velho/novo/'`). `awk` foca em tabular e extrair colunas de registros estruturados, como em `/etc/passwd`.
* **Manipulação Física:** `sort` (ordena linhas), `uniq` (remove duplicatas sequenciais), `wc` (conta linhas, palavras ou bytes) e `cut` (fatia colunas de texto).

**Redirecionamentos:**
O operador `>` sobrescreve o arquivo de destino com os novos dados; `>>` apenas anexa ao final. O pipe `|` encaminha a saída de um comando diretamente como entrada do próximo.

***

# 7. Operações com Conexões de Rede

O Linux opera nativamente com IPv4 e IPv6. O DNS traduz nomes de domínio para endereços IP numéricos que o kernel consegue processar.

* **Análise de Conexão:**
  * `ping` diagnostica conectividade usando pacotes ICMP para medir tempo de resposta.
  * `ip addr` (e o descontinuado `ifconfig`) configuram interfaces de rede e consultam IPs e status de tráfego.
  * `traceroute` lista cada salto (roteador) percorrido até o destino na internet.
* **Transferência e Conexão Remota:**
  * O **SSH** (`ssh usuario@servidor`) é o protocolo seguro padrão para controle remoto de servidores. Seus sub-protocolos **SCP** e **SFTP** realizam transferências de arquivos criptografadas.
  * `wget` e `curl` permitem downloads automatizados e requisições HTTP a APIs diretamente do terminal.

***

# 8. Bash e Scripting

Shell scripts permitem automatizar tarefas repetitivas encadeando comandos que seriam exaustivos de executar manualmente.

Todo script bash bem estruturado começa com a linha *shebang* (`#!/bin/bash`), que garante a execução pelo interpretador correto. Para ser executável, o arquivo precisa receber permissão com `chmod +x`.

**Conceitos Estruturais:**
* **Variáveis Especiais:** Scripts aceitam parâmetros da linha de comando via `$1` a `$9`. `$0` retorna o nome do script, `$#` indica a quantidade de parâmetros recebidos e `$?` contém o código de saída (exit code) do último comando executado.
* **Condicionais e Testes:** A estrutura `if` testa condições com operadores específicos para arquivos: `-d` (verifica se é um diretório), `-f` (arquivo comum) e `-z` (verifica se uma string está vazia).
* **Laços de Repetição:** `for` itera sobre listas de itens ou nomes de arquivos. `while` repete um bloco enquanto uma condição for verdadeira.

## 8.1 Shell Script Avançado

O nível avançado inclui manipulação de arrays, operadores booleanos e a estrutura `case`, que avalia de forma clara se uma variável corresponde a uma dentre várias possibilidades — útil, por exemplo, para processar argumentos de inicialização em serviços em segundo plano.

Para depurar scripts, usa-se a flag `set -x`, que ativa o modo de debug imprimindo a expansão de cada comando linha por linha durante a execução; `set +x` desativa esse recurso. Outro recurso comum é redirecionar saídas indesejadas para `/dev/null`, que descarta completamente qualquer texto ou log sem gravar nada em disco.

***

# 9. Segurança e Impressão

### Impressão (CUPS)
O Linux usa a plataforma **CUPS** (Common Unix Printing System) para gerenciar impressão. O sistema suporta rede, convertendo protocolos para serviços locais ou baseados na web. Os comandos `lp` e `lpr` enviam trabalhos de impressão; `lpq` monitora as filas ativas. Formatadores como `enscript` convertem arquivos ASCII e texto simples para PostScript. Para documentos PDF, o pacote `pdftk` permite dividir, reorganizar, mesclar e criptografar arquivos com proteção por senha.

### Fundamentos de Segurança Local
A arquitetura do Linux se baseia no **Princípio do Menor Privilégio** e no isolamento de memória entre processos. As contas de usuário são definidas em `/etc/passwd`, enquanto as senhas — cifradas no formato SHA-512 — ficam protegidas em `/etc/shadow`.

O módulo **PAM (Pluggable Authentication Modules)** centraliza políticas de autenticação, incluindo expiração obrigatória de senhas, integrado ao utilitário `chage` para controle de vencimento.

Manter o sistema atualizado é a principal medida de segurança: administradores garantem a integridade do ambiente monitorando logs em `/var/log/auth.log` e executando `apt update` regularmente, evitando CVEs decorrentes de versões desatualizadas.

***

> **Nota Adicional do Documento Unificado:** Todo o conteúdo deste documento é uma síntese integrada do programa LFS101 — *Introduction to Linux* pela *Linux Foundation*, elaborada com finalidade pedagógica para a compreensão abrangente da administração de ambientes GNU/Linux.

## 🔗 Recursos Úteis Adicionais

* [Página de Manuais e Configurações (man7)](https://man7.org/linux/man-pages/)
* [The Linux Documentation Project (TLDP)](https://tldp.org)
* [Ubuntu Wiki e Fóruns Oficiais](https://askubuntu.com)
* [Arch Linux Wiki (Referência Universal de Subsistemas)](https://wiki.archlinux.org)
* [Verificador de Scripts Shell (ShellCheck)](https://shellcheck.net)
