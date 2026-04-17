# Resumo Completo — Introduction to Linux (LFS101)
**Linux Foundation | Curso Gratuito | 60 horas | Nível: Iniciante**

> Este documento resume os 18 capítulos do curso LFS101 da Linux Foundation, cobrindo desde a história do Linux até segurança local e shell scripting avançado.

---

## Capítulo 1 — The Linux Foundation

A Linux Foundation é uma organização sem fins lucrativos fundada em 2000, com a missão de proteger e padronizar o desenvolvimento do kernel Linux. Ela atua como guardiã do ecossistema open source, provendo recursos para desenvolvedores e empresas.

**Principais pontos:**
- Papel da Linux Foundation no desenvolvimento e manutenção do kernel Linux
- Projetos hospedados: Kubernetes, Node.js, Hyperledger, ONAP, entre outros
- Programa de treinamento e certificações (LFCS, CKA, CKAD, etc.)
- A importância do Linux no mundo moderno: servidores, nuvem, dispositivos embarcados, smartphones (Android), supercomputadores e IoT
- Contribuição colaborativa entre empresas como Red Hat, IBM, Intel, Google, Samsung e comunidade

---

## Capítulo 2 — Linux Philosophy and Concepts

Introdução à filosofia que orienta o Linux e ao ecossistema de distribuições.

**Principais pontos:**
- **História:** Linus Torvalds criou o kernel Linux em 1991, inspirado no MINIX e no Unix. Richard Stallman e o projeto GNU forneceram as ferramentas de espaço de usuário
- **Licença:** O kernel é licenciado sob a GPL v2 (GNU General Public License), garantindo que o código-fonte seja aberto e redistribuível
- **Filosofia Unix/Linux:** "Faça uma coisa e faça bem", programas pequenos que se combinam via pipes e redirecionamentos
- **Distribuições Linux:** Uma distro empacota o kernel Linux com bibliotecas, ferramentas e um gerenciador de pacotes. Exemplos: Debian, Ubuntu, Fedora, RHEL, openSUSE, Arch
- **Famílias de distribuições:**
  - **Debian/Ubuntu:** usa `.deb` e `apt`
  - **Red Hat/Fedora/CentOS:** usa `.rpm` e `dnf`/`yum`
  - **SUSE:** usa `.rpm` e `zypper`
- **Kernel vs. Distribuição:** O kernel é o núcleo; a distro é o sistema completo pronto para uso
- **Open Source:** Modelo de desenvolvimento colaborativo que permite auditoria, modificação e redistribuição

---

## Capítulo 3 — Linux Basics and System Startup

Como o sistema Linux inicializa e os conceitos fundamentais de estrutura do sistema.

**Principais pontos:**
- **BIOS/UEFI:** Firmware que realiza o POST (Power-On Self Test) e transfere controle ao bootloader
- **Bootloader (GRUB2):** Grand Unified Bootloader v2; responsável por localizar o kernel no disco e carregá-lo na memória. Permite escolher entre múltiplos kernels ou sistemas operacionais
- **Kernel Initialization:** O kernel é descomprimido, detecta hardware, inicializa drivers e monta o sistema de arquivos raiz
- **`initramfs` / `initrd`:** Sistema de arquivos temporário em RAM usado durante o boot para montar o sistema de arquivos real
- **`systemd`:** Sistema de init moderno que substituiu o SysVinit. Gerencia serviços em paralelo, tornando o boot mais rápido. Usa "units" e "targets" (equivalentes aos runlevels)
- **Runlevels / Targets systemd:**
  - `poweroff.target` (0) — desligar
  - `rescue.target` (1) — modo single-user
  - `multi-user.target` (3) — modo texto com rede
  - `graphical.target` (5) — modo gráfico
  - `reboot.target` (6) — reiniciar
- **Comandos essenciais:** `systemctl start/stop/status/enable/disable <serviço>`
- **`/sbin/init`:** Primeiro processo a ser executado (PID 1); hoje geralmente é um link simbólico para o systemd
- **Sistemas de arquivos:** Ext4, XFS, Btrfs, FAT32; montagem via `/etc/fstab`

---

## Capítulo 4 — Graphical Interface

Exploração do ambiente gráfico do Linux.

**Principais pontos:**
- **X Window System (X11):** Base do sistema gráfico no Linux; separa servidor gráfico de aplicações clientes, permitindo exibição remota
- **Wayland:** Protocolo moderno que substitui o X11, mais seguro e eficiente; adotado por padrão no GNOME e em algumas versões do KDE
- **Desktop Environments:**
  - **GNOME:** Interface moderna e simplificada, padrão no Ubuntu e Fedora
  - **KDE Plasma:** Altamente customizável, visual similar ao Windows
  - **Xfce:** Leve e eficiente para hardware mais antigo
  - **LXDE/LXQt:** Ultra-leve
- **Display Manager:** Tela de login gráfico (GDM para GNOME, SDDM para KDE, LightDM)
- **Gerenciador de janelas:** Controla posição, tamanho e decoração das janelas
- **Operações básicas:** Iniciar aplicativos, criar atalhos no desktop, navegar pelo sistema de arquivos com o gerenciador de arquivos (Nautilus, Dolphin, Thunar)
- **Sessão gráfica vs. terminal:** Como abrir um terminal emulador dentro do ambiente gráfico (GNOME Terminal, Konsole, xterm)
- **Configurações de tela:** Resolução, múltiplos monitores, brilho, protetor de tela

---

## Capítulo 5 — System Configuration from the Graphical Interface

Configuração do sistema usando as ferramentas gráficas disponíveis.

**Principais pontos:**
- **Configurações de Sistema, Display, Data e Hora:**
  - Ajuste de fuso horário via interface gráfica
  - Sincronização via NTP (Network Time Protocol)
  - Configuração de idioma, teclado e região
- **Network Manager:**
  - Ferramenta para gerenciar conexões de rede com e sem fio via interface gráfica
  - Configuração de IP estático e DHCP
  - VPN, proxy e conexões PPPoE
- **Instalação e Atualização de Software:**
  - **GNOME Software / Discover:** Lojas de aplicativos gráficas
  - **Synaptic:** Gerenciador de pacotes gráfico para sistemas Debian/Ubuntu
  - Atualização do sistema inteiro via interface gráfica
  - Repositórios de software: como adicionar PPAs (Ubuntu) e repositórios externos
- **Gerenciamento de usuários:** Adicionar/remover usuários e grupos pela interface gráfica
- **Impressoras:** Configuração via CUPS (Common Unix Printing System) pela interface gráfica

---

## Capítulo 6 — Common Applications

Aplicações de uso cotidiano disponíveis no Linux.

**Principais pontos:**
- **Aplicações de Internet:**
  - Navegadores: Firefox, Chromium, Google Chrome
  - Clientes de e-mail: Thunderbird, Evolution
  - Clientes de mensagens: Pidgin, Empathy, Signal
  - Clientes FTP: FileZilla
- **Produtividade e Desenvolvimento:**
  - **LibreOffice:** Suite completa com Writer (texto), Calc (planilhas), Impress (apresentações), compatível com formatos MS Office
  - **GIMP:** Editor de imagens rasterizadas (alternativa ao Photoshop)
  - **Inkscape:** Editor de gráficos vetoriais (SVG)
  - Editores de código: VS Code, Gedit, Kate, Sublime Text
- **Aplicações Multimídia:**
  - Reprodutores de vídeo: VLC, Totem (GNOME Videos)
  - Reprodutores de áudio: Rhythmbox, Amarok, Audacious
  - Edição de áudio: Audacity
  - Streaming: Spotify (cliente nativo disponível)
- **Utilitários gráficos:**
  - Visualizador de PDF: Evince, Okular
  - Captura de tela: GNOME Screenshot, Flameshot
  - Gerenciador de arquivos: Nautilus (GNOME), Dolphin (KDE)
- **Virtualização:** VirtualBox, GNOME Boxes

---

## Capítulo 7 — Command Line Operations

Operações fundamentais via linha de comando — o coração do Linux.

**Principais pontos:**
- **Shell:** Interface de linha de comando; o mais comum é o **bash** (Bourne Again Shell)
- **Terminal Emulador:** Aplicativo que fornece acesso ao shell dentro do ambiente gráfico
- **Modos de comando:**
  - TTY (terminal virtual): `Ctrl+Alt+F2` a `F6`
  - Terminal emulado no modo gráfico
- **Operações básicas:**
  - `ls` — listar arquivos e diretórios
  - `cd` — mudar de diretório
  - `pwd` — exibir diretório atual
  - `mkdir` / `rmdir` — criar / remover diretórios
  - `cp` / `mv` / `rm` — copiar, mover, remover arquivos
  - `cat` / `less` / `more` — exibir conteúdo de arquivos
  - `echo` — imprimir texto
  - `man` — manual dos comandos
- **Trabalhando com arquivos:**
  - `touch` — criar arquivo vazio ou atualizar timestamp
  - `file` — identificar tipo de arquivo
  - `stat` — informações detalhadas de arquivo
  - `wc` — contar linhas, palavras, caracteres
- **Busca de arquivos:**
  - `find` — busca por nome, tipo, tamanho, data
  - `locate` — busca rápida usando banco de dados (`updatedb`)
  - `which` / `whereis` — localizar executáveis
- **Instalação de software via linha de comando:**
  - `apt install` (Debian/Ubuntu)
  - `dnf install` / `yum install` (Red Hat/Fedora)
  - `zypper install` (SUSE)
- **Wildcards:** `*`, `?`, `[abc]` para expansão de nomes
- **Redirecionamento e pipes:**
  - `>` — redirecionar saída para arquivo
  - `>>` — acrescentar ao arquivo
  - `<` — entrada a partir de arquivo
  - `|` — encadear comandos (pipe)
- **Variáveis de ambiente:** `$HOME`, `$PATH`, `$USER`, `export`, `env`
- **Histórico de comandos:** `history`, `!!`, `!n`, `Ctrl+R`

---

## Capítulo 8 — Finding Linux Documentation

Como encontrar ajuda e documentação dentro do próprio sistema Linux.

**Principais pontos:**
- **`man` (Manual Pages):**
  - Estrutura: NAME, SYNOPSIS, DESCRIPTION, OPTIONS, EXAMPLES, SEE ALSO
  - Seções: 1 (comandos de usuário), 2 (syscalls), 3 (funções C), 5 (arquivos de configuração), 8 (administração)
  - `man -k <palavra>` — buscar por palavra-chave (equivalente a `apropos`)
- **GNU Info (`info`):**
  - Sistema de documentação mais completo que o man, com hiperlinks e navegação
  - `info <comando>` — abre a documentação info
- **Opção `--help`:**
  - Quase todos os comandos suportam `--help` ou `-h` para um resumo rápido de uso
- **Comando `help`:**
  - Para comandos internos do bash (`help cd`, `help echo`)
- **Outras fontes de documentação:**
  - `/usr/share/doc/` — documentação local instalada com pacotes
  - Páginas de projeto: wikis, README, CHANGELOG
  - **The Linux Documentation Project (TLDP):** tldp.org — HOWTOs, guias e FAQs
  - **Stack Overflow / Ask Ubuntu / Unix & Linux StackExchange**
  - **Arch Wiki** — considerada uma das melhores wikis de Linux (útil para qualquer distro)
  - Listas de e-mail e fóruns das distribuições

---

## Capítulo 9 — Processes

Gerenciamento de processos no Linux.

**Principais pontos:**
- **O que é um processo:** Instância de um programa em execução, com seu próprio espaço de memória e PID (Process ID)
- **Atributos de processo:**
  - PID (Process ID), PPID (Parent PID), UID/GID (usuário/grupo dono)
  - Estado: Running (R), Sleeping (S), Stopped (T), Zombie (Z)
  - Prioridade/Nice value (-20 a +19)
- **Comandos de monitoramento:**
  - `ps aux` — lista todos os processos em execução
  - `ps -ef` — formato alternativo com PPID
  - `top` — monitor interativo em tempo real (CPU, memória, carga)
  - `htop` — versão aprimorada e colorida do top
  - `pstree` — visualiza hierarquia de processos em árvore
- **Controle de processos:**
  - `kill <PID>` — enviar sinal a um processo (padrão: SIGTERM)
  - `kill -9 <PID>` — força o encerramento (SIGKILL)
  - `killall <nome>` — matar todos os processos com determinado nome
  - `pkill <padrão>` — matar por padrão de nome
  - `Ctrl+C` — interromper processo em primeiro plano (SIGINT)
  - `Ctrl+Z` — suspender processo (SIGTSTP)
- **Foreground e Background:**
  - `<comando> &` — executar em background
  - `jobs` — listar processos em background
  - `bg` / `fg` — mover processo para background/foreground
- **Agendamento de processos:**
  - `at` — executar comando uma vez em horário específico
  - `cron` / `crontab` — agendamento recorrente (minuto, hora, dia, mês, dia da semana)
  - `sleep` — pausar execução por N segundos
- **`nice` e `renice`:** Ajustar prioridade de processos
- **`/proc`:** Sistema de arquivos virtual com informações em tempo real sobre processos e o kernel

---

## Capítulo 10 — File Operations

Sistema de arquivos e operações com arquivos no Linux.

**Principais pontos:**
- **Sistemas de arquivos Linux:**
  - **ext4:** Padrão na maioria das distros, journaling, suporta volumes de até 1 EB
  - **XFS:** Alta performance para grandes arquivos, usado no RHEL/CentOS
  - **Btrfs:** Copy-on-write, snapshots, checksums
  - **tmpfs:** Sistema de arquivos em memória RAM
  - **NFS/SMB:** Sistemas de arquivos de rede
- **Hierarquia de diretórios (FHS — Filesystem Hierarchy Standard):**
  - `/` — raiz do sistema
  - `/bin`, `/usr/bin` — executáveis essenciais
  - `/sbin`, `/usr/sbin` — executáveis de administração
  - `/etc` — arquivos de configuração
  - `/home` — diretórios pessoais dos usuários
  - `/root` — home do root
  - `/var` — dados variáveis (logs, spool, cache)
  - `/tmp` — arquivos temporários
  - `/dev` — dispositivos
  - `/proc`, `/sys` — pseudossistemas de arquivos do kernel
  - `/mnt`, `/media` — pontos de montagem
  - `/lib`, `/usr/lib` — bibliotecas compartilhadas
  - `/boot` — kernel e bootloader
- **Montagem de sistemas de arquivos:**
  - `mount` / `umount`
  - `/etc/fstab` — montagem automática no boot
  - `df -h` — uso de espaço em disco
  - `du -sh` — tamanho de diretórios
- **Comparação de arquivos:**
  - `diff` — diferenças entre arquivos texto
  - `md5sum` / `sha256sum` — verificar integridade
  - `cmp` — comparação byte a byte
- **Tipos de arquivos:**
  - Regular, diretório, link simbólico, dispositivo de bloco, dispositivo de caractere, socket, pipe (FIFO)
  - `file <arquivo>` — identifica o tipo
  - `ln -s` — cria link simbólico; `ln` — cria hard link
- **Backup e Compressão:**
  - `tar` — empacotamento de arquivos (`.tar`, `.tar.gz`, `.tar.bz2`, `.tar.xz`)
  - `gzip` / `gunzip`, `bzip2`, `xz` — compressão
  - `zip` / `unzip` — formato ZIP
  - `rsync` — sincronização eficiente de arquivos e backups incrementais
- **Permissões de arquivo:**
  - Leitura (r=4), Escrita (w=2), Execução (x=1)
  - `chmod` — alterar permissões (simbólico ou octal)
  - `chown` — alterar dono e grupo
  - `umask` — máscara padrão de permissões para novos arquivos

---

## Capítulo 11 — Text Editors

Editores de texto disponíveis no Linux, do mais simples ao mais avançado.

**Principais pontos:**
- **nano:**
  - Editor simples, ideal para iniciantes
  - Atalhos exibidos na parte inferior da tela
  - Operações: `Ctrl+O` salvar, `Ctrl+X` sair, `Ctrl+K` cortar linha, `Ctrl+U` colar
- **gedit:**
  - Editor gráfico padrão do GNOME
  - Suporte a syntax highlighting, plugins, busca e substituição
  - Ideal para edição rápida com interface gráfica
- **vi / vim:**
  - Editor histórico do Unix, presente em praticamente todo sistema Linux
  - **Modos:** Normal (navegação e comandos), Insert (digitação), Visual (seleção), Command-line (`:`)
  - Comandos essenciais:
    - `i` — entrar no modo insert
    - `Esc` — voltar ao modo normal
    - `:w` — salvar; `:q` — sair; `:wq` — salvar e sair; `:q!` — sair sem salvar
    - `dd` — deletar linha; `yy` — copiar linha; `p` — colar
    - `/padrão` — buscar; `n` — próxima ocorrência
    - `u` — desfazer; `Ctrl+R` — refazer
  - `vimtutor` — tutorial interativo integrado
- **emacs:**
  - Editor extremamente extensível, com ecossistema próprio de plugins (LISP)
  - Pode funcionar como IDE, cliente de e-mail, gerenciador de arquivos
  - Atalhos baseados em `Ctrl` e `Meta (Alt)`
  - `C-x C-s` salvar, `C-x C-c` sair, `C-g` cancelar comando

---

## Capítulo 12 — User Environment

Configuração e personalização do ambiente de usuário no Linux.

**Principais pontos:**
- **Contas de usuário:**
  - `whoami` — usuário atual
  - `id` — UID, GID e grupos
  - `/etc/passwd` — banco de dados de usuários
  - `/etc/shadow` — senhas criptografadas
  - `/etc/group` — grupos do sistema
- **Gerenciamento de usuários:**
  - `useradd` / `userdel` / `usermod` — criar, remover, modificar usuários
  - `groupadd` / `groupdel` / `groupmod` — gerenciar grupos
  - `passwd` — alterar senha
  - `su` — trocar de usuário; `su -` — login completo como outro usuário
  - `sudo` — executar comandos como root; configuração em `/etc/sudoers`
- **Variáveis de ambiente:**
  - `$HOME`, `$PATH`, `$SHELL`, `$USER`, `$LANG`, `$TERM`
  - `export VAR=valor` — definir e exportar variável
  - `env` — listar todas variáveis de ambiente
  - `printenv <VAR>` — exibir valor de variável
- **Arquivos de configuração do shell (bash):**
  - `/etc/profile` — executado para todos os usuários no login
  - `~/.bash_profile` ou `~/.profile` — configuração de login do usuário
  - `~/.bashrc` — executado para shells interativos não-login
  - `~/.bash_logout` — executado ao sair
  - `~/.bash_history` — histórico de comandos
- **Aliases:**
  - `alias ll='ls -la'` — criar atalho de comando
  - `unalias` — remover alias
- **Customização do prompt (PS1):**
  - Variável `$PS1` controla o formato do prompt
  - Sequências especiais: `\u` (usuário), `\h` (hostname), `\w` (diretório atual)
- **`which` e `type`:** Descobrir o tipo e localização de um comando

---

## Capítulo 13 — Manipulating Text

Ferramentas para processar, filtrar e transformar texto na linha de comando.

**Principais pontos:**
- **`cat`:** Concatenar e exibir arquivos; `-n` numera linhas
- **`tac`:** Exibir arquivo em ordem inversa (última linha primeiro)
- **`head` / `tail`:**
  - `head -n 20 arquivo` — primeiras 20 linhas
  - `tail -n 20 arquivo` — últimas 20 linhas
  - `tail -f arquivo` — monitorar arquivo em tempo real (útil para logs)
- **`less` / `more`:** Paginadores para visualizar arquivos longos
- **`grep`:**
  - Busca por padrão em arquivos: `grep "padrão" arquivo`
  - `-i` case-insensitive; `-r` recursivo; `-n` número de linha; `-v` inverso (excluir)
  - `-E` expressões regulares estendidas
- **`sed` (Stream Editor):**
  - Substituição: `sed 's/antigo/novo/g' arquivo`
  - Deleção de linhas: `sed '/padrão/d'`
  - Edição in-place: `sed -i 's/a/b/g' arquivo`
- **`awk`:**
  - Linguagem de processamento de texto por colunas
  - `awk '{print $1}' arquivo` — imprime primeira coluna
  - `awk -F: '{print $1}' /etc/passwd` — usa `:` como separador
  - Suporte a condicionais, loops e funções
- **`sort`:** Ordenar linhas; `-n` numérico; `-r` reverso; `-u` remover duplicatas
- **`uniq`:** Remover linhas duplicadas consecutivas; `-c` contar ocorrências
- **`cut`:** Extrair colunas: `cut -d: -f1 /etc/passwd`
- **`paste`:** Juntar arquivos lado a lado por coluna
- **`tr`:** Substituir ou deletar caracteres: `tr 'a-z' 'A-Z'` (converter para maiúsculas)
- **`wc`:** Contar linhas (`-l`), palavras (`-w`), bytes (`-c`)
- **`split`:** Dividir arquivos grandes em partes menores
- **Expressões regulares:** `.` (qualquer char), `*`, `+`, `?`, `^` (início), `$` (fim), `[abc]`, `\d`, etc.
- **`strings`:** Extrair strings legíveis de arquivos binários

---

## Capítulo 14 — Network Operations

Configuração e diagnóstico de rede no Linux.

**Principais pontos:**
- **Conceitos básicos de rede:**
  - Endereço IP (IPv4 e IPv6), máscara de rede, gateway, DNS
  - Interfaces de rede: `eth0`, `ens33`, `wlan0`, `lo` (loopback)
- **Configuração de rede:**
  - `ip addr` — exibir endereços IP (substitui `ifconfig`)
  - `ip link` — estado das interfaces
  - `ip route` — tabela de roteamento
  - `ifconfig` — ferramenta legada (ainda disponível via `net-tools`)
  - `nmcli` — interface CLI do NetworkManager
  - `/etc/hosts` — resolução local de nomes
  - `/etc/resolv.conf` — servidores DNS configurados
  - `/etc/network/interfaces` (Debian) ou `/etc/sysconfig/network-scripts/` (Red Hat)
- **Diagnóstico de rede:**
  - `ping` — testar conectividade ICMP
  - `traceroute` / `tracepath` — rastrear rota de pacotes
  - `mtr` — combinação de ping e traceroute interativo
  - `nslookup` / `dig` — consultar servidores DNS
  - `host` — resolver nomes de domínio
  - `netstat` / `ss` — listar conexões de rede ativas, portas abertas
  - `nmap` — scanner de portas e hosts
- **Transferência de arquivos e acesso remoto:**
  - `ssh` — acesso remoto seguro: `ssh usuario@host`
  - `scp` — cópia segura: `scp arquivo usuario@host:/destino`
  - `sftp` — FTP seguro via SSH
  - `rsync` — sincronização eficiente via rede ou local
  - `wget` — download de arquivos via HTTP/FTP
  - `curl` — transferência de dados com suporte a múltiplos protocolos, útil para APIs REST
- **Firewall:**
  - `firewalld` (Red Hat/Fedora): `firewall-cmd`
  - `ufw` (Ubuntu): `ufw allow 22/tcp`
  - `iptables` — ferramenta legada de filtragem de pacotes

---

## Capítulo 15 — The Bash Shell and Basic Scripting

Introdução ao shell Bash e à criação de scripts básicos.

**Principais pontos:**
- **O que é um shell script:** Arquivo de texto com sequência de comandos bash executáveis
- **Shebang:** Primeira linha do script: `#!/bin/bash` indica o interpretador
- **Permissão de execução:** `chmod +x script.sh`; executar com `./script.sh` ou `bash script.sh`
- **Variáveis:**
  - Definição: `NOME="valor"` (sem espaços)
  - Uso: `echo $NOME` ou `echo ${NOME}`
  - Variáveis especiais: `$0` (nome do script), `$1..$9` (argumentos), `$#` (número de args), `$@` (todos os args), `$?` (código de retorno do último comando), `$$` (PID do script)
- **Entrada do usuário:** `read -p "Digite algo: " VARIAVEL`
- **Substituição de comandos:**
  - `$(comando)` ou `` `comando` ``
  - Exemplo: `DATA=$(date +%Y-%m-%d)`
- **Operações aritméticas:** `$(( expressão ))` ou `let "x = 5 + 3"`
- **Condicionais:**
  ```bash
  if [ condição ]; then
    comandos
  elif [ condição ]; then
    comandos
  else
    comandos
  fi
  ```
  - Operadores de comparação numérica: `-eq`, `-ne`, `-lt`, `-le`, `-gt`, `-ge`
  - Operadores de string: `=`, `!=`, `-z` (vazia), `-n` (não vazia)
  - Operadores de arquivo: `-f` (arquivo regular), `-d` (diretório), `-e` (existe), `-r` (legível), `-x` (executável)
- **Loops:**
  ```bash
  for i in 1 2 3; do echo $i; done
  for arquivo in *.txt; do echo $arquivo; done
  while [ condição ]; do comandos; done
  until [ condição ]; do comandos; done
  ```
- **`case`:**
  ```bash
  case $VAR in
    padrão1) comandos ;;
    padrão2) comandos ;;
    *) default ;;
  esac
  ```
- **Funções:**
  ```bash
  minha_funcao() {
    echo "Olá, $1"
  }
  minha_funcao "mundo"
  ```
- **Boas práticas:** Comentários com `#`, nomes descritivos de variáveis, verificar códigos de retorno

---

## Capítulo 16 — More on Bash Shell Scripting

Técnicas avançadas de shell scripting.

**Principais pontos:**
- **Expressões regulares em scripts:** Uso com `grep`, `sed`, `awk` dentro de scripts
- **Manipulação avançada de strings:**
  - `${#VAR}` — comprimento da string
  - `${VAR:offset:length}` — substring
  - `${VAR/antigo/novo}` — substituição
  - `${VAR^^}` / `${VAR,,}` — maiúsculas/minúsculas (bash 4+)
- **Arrays:**
  ```bash
  arr=("a" "b" "c")
  echo ${arr[0]}
  echo ${arr[@]}   # todos os elementos
  echo ${#arr[@]}  # tamanho do array
  ```
- **Tratamento de erros:**
  - `set -e` — abortar script em caso de erro
  - `set -u` — abortar ao usar variável não definida
  - `trap 'comando' SIGNAL` — capturar sinais e erros
  - `trap 'rm -f /tmp/tmpfile' EXIT` — limpeza ao sair
- **Depuração de scripts:**
  - `bash -x script.sh` — modo debug (imprime cada comando antes de executar)
  - `set -x` dentro do script; `set +x` para desligar
- **Redirecionamento avançado:**
  - `2>` — redirecionar stderr
  - `2>&1` — combinar stderr com stdout
  - `/dev/null` — descartar saída
  - `tee` — redirecionar para arquivo e stdout simultaneamente
- **Here Document (heredoc):**
  ```bash
  cat << EOF
  Texto multilinha
  EOF
  ```
- **Processos em subshell:** `(comandos)` — executa em subshell isolado
- **`eval`:** Executar string como comando
- **`exec`:** Substituir processo atual por outro
- **`getopts`:** Processar opções de linha de comando em scripts
- **Scripts mais robustos:** Validação de entrada, verificação de dependências, logging com timestamp

---

## Capítulo 17 — Printing

Configuração e gerenciamento de impressão no Linux.

**Principais pontos:**
- **CUPS (Common Unix Printing System):**
  - Sistema de impressão padrão no Linux
  - Interface web de administração: `http://localhost:631`
  - Suporte a impressoras locais (USB, paralela) e de rede (IPP, LPD, SMB)
- **Gerenciamento de impressoras:**
  - `lpstat -p` — listar impressoras configuradas
  - `lpadmin` — adicionar/configurar impressoras
  - Configuração gráfica via Configurações do Sistema
- **Comandos de impressão:**
  - `lp arquivo.pdf` — imprimir arquivo
  - `lp -n 3 arquivo` — imprimir 3 cópias
  - `lp -P 1-5 arquivo` — imprimir páginas específicas
  - `lpr` — alternativa ao `lp` (compatível com BSD)
- **Fila de impressão:**
  - `lpq` — verificar fila de impressão
  - `lprm <job_id>` — cancelar trabalho de impressão
  - `cancel` — cancelar impressão (alternativa do CUPS)
- **Conversão de formatos para impressão:**
  - `enscript` — converter texto para PostScript
  - `ps2pdf` — converter PostScript para PDF
  - `pdftops` — converter PDF para PostScript
  - `evince`, `okular` — visualizadores de PDF com suporte a impressão
- **`a2ps`:** Formatar texto ASCII para impressão com cabeçalhos e bordas
- **Drivers de impressora:** PPD (PostScript Printer Description), Foomatic

---

## Capítulo 18 — Local Security Principles

Princípios e práticas de segurança local no Linux.

**Principais pontos:**
- **Conceito de privilégio mínimo:** Usuários e processos devem ter apenas as permissões necessárias para sua função
- **Conta root:**
  - Root tem controle total sobre o sistema; deve ser usado apenas quando necessário
  - Nunca fazer login diretamente como root em ambiente de produção
  - Preferir `sudo` para comandos específicos
- **`sudo`:**
  - Permite a usuários comuns executar comandos com privilégios elevados
  - Configuração em `/etc/sudoers` (editar com `visudo`)
  - Log de todos os comandos executados com sudo em `/var/log/auth.log` ou `/var/log/secure`
- **Permissões de arquivo e segurança:**
  - Bits especiais: **SUID** (executa com privilégio do dono), **SGID** (executa com privilégio do grupo), **Sticky bit** (apenas o dono pode deletar em diretório compartilhado, ex: `/tmp`)
  - `find / -perm -4000` — localizar arquivos SUID no sistema
- **Senhas e autenticação:**
  - `/etc/passwd` — informações de usuário (senhas não ficam aqui)
  - `/etc/shadow` — senhas hashed (SHA-512), acessível apenas pelo root
  - Políticas de senha: validade, comprimento mínimo via PAM (`/etc/pam.d/`)
  - `chage` — gerenciar expiração de senha
- **PAM (Pluggable Authentication Modules):**
  - Framework de autenticação modular
  - Controla autenticação, autorização, sessão e gestão de senhas
  - Configuração em `/etc/pam.d/`
- **Criptografia de dados:**
  - LUKS (Linux Unified Key Setup) — criptografia de disco completo
  - `dm-crypt` — dispositivos de bloco criptografados
  - `gpg` — criptografia de arquivos individuais (PGP)
  - `openssl` — criptografia via linha de comando
- **Logs de segurança:**
  - `/var/log/auth.log` (Debian/Ubuntu) ou `/var/log/secure` (Red Hat)
  - `/var/log/syslog` ou `/var/log/messages` — log geral do sistema
  - `journalctl` — consultar logs do systemd
  - `last` — histórico de logins
  - `who` / `w` — usuários logados no momento
- **Atualizações de segurança:**
  - Manter o sistema atualizado é a medida de segurança mais importante
  - `apt upgrade` / `dnf update` — atualizar pacotes
  - Verificar CVEs (Common Vulnerabilities and Exposures) para softwares utilizados
- **Firewall básico:**
  - `ufw` (Ubuntu): `ufw enable`, `ufw allow ssh`
  - `firewall-cmd` (Red Hat): gerenciar zonas e serviços
- **`chroot`:** Isolar processos em um subdiretório como raiz falsa (sandbox básico)
- **SELinux e AppArmor:**
  - **SELinux** (Security-Enhanced Linux): controle de acesso mandatório, padrão no Red Hat/Fedora
  - **AppArmor:** perfis de segurança por aplicação, padrão no Ubuntu/SUSE
  - Modos: enforcing, permissive, disabled

---

## Resumo Geral do Curso

| Capítulo | Tema Principal |
|---|---|
| 1 | Linux Foundation e ecossistema open source |
| 2 | Filosofia Linux, distros e licenciamento |
| 3 | Boot, kernel, systemd e inicialização |
| 4 | Interface gráfica, GNOME, KDE, Wayland |
| 5 | Configuração do sistema via GUI |
| 6 | Aplicações comuns (internet, produtividade, multimídia) |
| 7 | Linha de comando: comandos essenciais |
| 8 | Documentação: man, info, --help |
| 9 | Processos: ps, top, kill, cron |
| 10 | Sistema de arquivos, permissões, backup |
| 11 | Editores de texto: nano, vim, emacs |
| 12 | Ambiente do usuário, variáveis, bash config |
| 13 | Manipulação de texto: grep, sed, awk, sort |
| 14 | Redes: ip, ssh, wget, curl, firewall |
| 15 | Shell scripting básico |
| 16 | Shell scripting avançado |
| 17 | Impressão com CUPS |
| 18 | Segurança local: sudo, permissões, PAM, SELinux |

---

*Fonte: Linux Foundation — Introduction to Linux (LFS101) | https://training.linuxfoundation.org/training/introduction-to-linux/*
