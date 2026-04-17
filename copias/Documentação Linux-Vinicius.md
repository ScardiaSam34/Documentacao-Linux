
# 🐧 Introdução ao Linux — LFS101 | Linux Foundation
### Resumo Completo e Detalhado — Capítulos 1 ao 18

---

## 📋 Tópicos

- [Cap. 1 — A Linux Foundation](#cap-1--a-linux-foundation)
- [Cap. 2 — Filosofia e Conceitos do Linux](#cap-2--filosofia-e-conceitos-do-linux)
- [Cap. 3 — Fundamentos e Inicialização do Sistema](#cap-3--fundamentos-e-inicialização-do-sistema)
- [Cap. 4 — Interface Gráfica](#cap-4--interface-gráfica)
- [Cap. 5 — Configuração do Sistema pela GUI](#cap-5--configuração-do-sistema-pela-gui)
- [Cap. 6 — Aplicações Comuns](#cap-6--aplicações-comuns)
- [Cap. 7 — Operações na Linha de Comando](#cap-7--operações-na-linha-de-comando)
- [Cap. 8 — Encontrando Documentação](#cap-8--encontrando-documentação)
- [Cap. 9 — Processos](#cap-9--processos)
- [Cap. 10 — Operações com Arquivos](#cap-10--operações-com-arquivos)
- [Cap. 11 — Editores de Texto](#cap-11--editores-de-texto)
- [Cap. 12 — Ambiente do Usuário](#cap-12--ambiente-do-usuário)
- [Cap. 13 — Manipulação de Texto](#cap-13--manipulação-de-texto)
- [Cap. 14 — Operações de Rede](#cap-14--operações-de-rede)
- [Cap. 15 — Shell Bash e Scripting Básico](#cap-15--shell-bash-e-scripting-básico)
- [Cap. 16 — Bash Shell Scripting Avançado](#cap-16--bash-shell-scripting-avançado)
- [Cap. 17 — Impressão](#cap-17--impressão)
- [Cap. 18 — Princípios de Segurança Local](#cap-18--princípios-de-segurança-local)
- [Recursos Úteis](#recursos-úteis)

---

## Cap. 1 — A Linux Foundation

### 1.1 Sobre a Linux Foundation

A **Linux Foundation** é uma organização sem fins lucrativos responsável por apoiar o desenvolvimento do kernel Linux e projetos de código aberto relacionados. Sua missão é fornecer experiência e expertise para iniciativas que buscam resolver problemas complexos por meio de colaboração open source.

> 💡 A Linux Foundation oferece ferramentas para escalar projetos: melhores práticas de segurança, governança, operações, treinamento e certificação.

### 1.2 Famílias de Distribuições

O curso foca nas três grandes famílias de distribuições Linux:

| Família | Distribuições | Gerenciador de Pacotes |
|---|---|---|
| 🔴 **Red Hat** | RHEL, CentOS, Fedora, Oracle Linux | `yum` / `dnf` |
| 🟢 **SUSE** | SUSE Linux Enterprise, openSUSE | `zypper` |
| 🟠 **Debian** | Debian, Ubuntu, Linux Mint | `apt` / `apt-get` |

### 1.3 Características por Família

**Família Red Hat**
- Suporta arquiteturas: Intel x86, ARM, Itanium, PowerPC, IBM System z
- Amplamente adotada em ambientes corporativos
- Fedora funciona como plataforma de testes *upstream* para o RHEL

**Família SUSE**
- Inclui o **YaST** (Yet Another Setup Tool) como ferramenta de administração
- Amplamente usada no setor de varejo

**Família Debian**
- Possui o maior repositório de software de qualquer distribuição Linux
- Ubuntu é amplamente usado em cloud computing, baseado no GNOME

---

## Cap. 2 — Filosofia e Conceitos do Linux

### 2.1 História

O Linux foi fortemente inspirado no **UNIX**. Acessa muitos recursos e serviços por meio de arquivos e objetos semelhantes a arquivos. É um sistema operacional completamente multi-tarefa e multi-usuário, desenvolvido por uma confederação descentralizada de desenvolvedores do mundo todo, com **Linus Torvalds** à frente.

### 2.2 Terminologia Fundamental

| Termo | Definição |
|---|---|
| **Kernel** | Núcleo do sistema operacional |
| **Distribuição** | Kernel + ferramentas e aplicações |
| **Boot Loader** | Programa que inicia o sistema operacional |
| **Daemon / Serviço** | Processo em segundo plano |
| **Sistema de Arquivos** | Método de organizar e localizar dados |
| **X Window System** | Sistema gráfico base do Linux |
| **Ambiente de Desktop** | GNOME, KDE, XFCE etc. |
| **Linha de Comando** | Interface textual de interação com o sistema |

### 2.3 Comunidade e Filosofia

- Desenvolvido via colaboração pela internet
- Habilidade técnica e vontade de contribuir são os únicos requisitos para participar
- Processos de serviço em segundo plano são chamados de **daemons**

### 2.4 Distribuições

Uma distribuição completa consiste em:

```
Kernel + ferramentas para:
  ├── Operações com arquivos
  ├── Gerenciamento de usuários
  └── Gerenciamento de pacotes
```

> 🏢 Grandes organizações tendem a escolher distribuições com suporte comercial da **Red Hat**, **SUSE** e **Canonical** (Ubuntu).

---

## Cap. 3 — Fundamentos e Inicialização do Sistema

### 3.1 Processo de Boot (Passo a Passo)

```
[POWER ON]
    │
    ▼
[BIOS / UEFI]  ──→  POST (Power On Self Test)
    │
    ▼
[Boot Loader]  ──→  MBR (512 bytes) ou Partição EFI
    │              Opções: GRUB, ISOLINUX, DAS U-Boot
    ▼
[Kernel]       ──→  Descomprimido, carregado na RAM
    │              Analisa hardware, inicializa drivers
    ▼
[initramfs]    ──→  Monta sistema de arquivos raiz
    │              udev detecta dispositivos
    ▼
[/sbin/init]   ──→  systemd (gerenciador de serviços)
    │
    ▼
[Sistema Pronto]
```

### 3.2 systemd

O **systemd** substituiu o antigo **SysVinit** (sequencial e serial), trazendo:

- ✅ Inicialização de serviços em **paralelo** → boot muito mais rápido
- ✅ Scripts complexos substituídos por arquivos de configuração simples
- ✅ `/sbin/init` agora aponta para `/lib/systemd/systemd`

**Comandos principais com `systemctl`:**

```bash
systemctl start   <serviço>   # Inicia um serviço
systemctl stop    <serviço>   # Para um serviço
systemctl restart <serviço>   # Reinicia um serviço
systemctl enable  <serviço>   # Habilita na inicialização
systemctl disable <serviço>   # Desabilita na inicialização
systemctl status  <serviço>   # Verifica status do serviço
```

### 3.3 Sistema de Arquivos

**Tipos suportados:**

| Categoria | Tipos |
|---|---|
| Convencionais | `ext3`, `ext4`, `XFS`, `Btrfs`, `JFS`, `NTFS`, `vfat`, `exfat` |
| Para Flash | `ubifs`, `jffs2`, `yaffs` |
| Especiais | `procfs`, `sysfs`, `tmpfs`, `squashfs` |

> 📌 O Linux organiza arquivos seguindo o padrão **FHS (Filesystem Hierarchy Standard)**, usando `/` para separar caminhos — sem letras de unidade como no Windows.

### 3.4 Instalação

**Considerações antes de instalar:**
- Servidor ou desktop?
- Espaço em disco necessário
- Ciclo de suporte da distribuição
- Arquitetura de hardware

**Métodos de instalação:**

| Método | Descrição |
|---|---|
| USB / CD / DVD | Instalação padrão por mídia física |
| Rede | Instalação via PXE ou servidor |
| Kickstart | Instalação automatizada (Red Hat) |
| AutoYAST | Instalação automatizada (SUSE) |
| Preseed | Instalação automatizada (Debian) |
| Dual Boot | Preserva outro sistema operacional |
| Virtualização | VMware, VirtualBox — sem afetar o sistema principal |

---

## Cap. 4 — Interface Gráfica

### 4.1 X Window System e Wayland

O sistema gráfico do Linux é baseado no **X Window System** ("X"), criado em meados dos anos 1980. O **Display Manager** gerencia telas disponíveis, carrega o servidor X e inicia o ambiente de desktop após o login.

| Sistema | Status |
|---|---|
| **X Window System** | Legado, ainda amplamente usado |
| **Wayland** | Moderno, mais seguro, já padrão no Fedora e RHEL 8+ |

**Display Managers populares:** `gdm` (GNOME), `lightdm`, `kdm`

### 4.2 Ambientes de Desktop

| Ambiente | Usado em | Característica |
|---|---|---|
| **GNOME** | RHEL, Fedora, Ubuntu, Debian | Mais popular, navegação por menus |
| **KDE** | SUSE, openSUSE | Rico em recursos, altamente configurável |
| **XFCE** | Várias distros | Leve, ideal para hardware antigo |
| **LXDE** | Várias distros | Ultra leve, baixíssimo consumo |

### 4.3 Personalização

- 🖼️ **Papel de parede:** clique direito no desktop → "Change Background"
- 🔧 **gnome-tweaks:** expõe opções avançadas não disponíveis no painel padrão
  - Instalar extensões de terceiros
  - Remapear teclas (ex: CapsLock → Ctrl)
- 🎨 **Temas:** controlam aparência de botões, barras de rolagem e janelas

### 4.4 Gerenciamento de Sessões

```bash
# Atalhos úteis
SUPER + L        # Bloquear tela (tecla Windows + L)
```

> 👥 O Linux é um verdadeiro sistema **multi-usuário** — mais de um usuário pode estar conectado simultaneamente sem encerrar sessões.

---

## Cap. 5 — Configuração do Sistema pela GUI

### 5.1 Painel de Configurações

- Gerenciamento de múltiplos monitores e resolução de tela
- Configuração de data e hora (manual ou via NTP)
- **NTP** (Network Time Protocol) — sincronização automática com servidores de tempo

### 5.2 Network Manager

Ferramenta para gerenciar conexões de rede:

| Tipo de Conexão | Suporte |
|---|---|
| Cabeada (Ethernet) | ✅ |
| Wi-Fi | ✅ |
| Banda Larga Móvel | ✅ |
| VPN | ✅ |

> 🌐 É possível configurar endereços **IP estáticos** manualmente nas configurações IPv4 de cada conexão.

### 5.3 Gerenciamento de Software pela GUI

| Distribuição | Ferramenta Gráfica |
|---|---|
| Ubuntu | Ubuntu Software Centre |
| CentOS / RHEL | PackageKit / GNOME Software |
| openSUSE | YaST Software Manager |

---

## Cap. 6 — Aplicações Comuns

### 6.1 Internet

| Categoria | Aplicações |
|---|---|
| Navegadores | Firefox, Chrome, Epiphany |
| E-mail | Thunderbird, Evolution |
| FTP | FileZilla, gFTP |
| Mensagens / IRC / VoIP | Pidgin, HexChat, Ekiga |

### 6.2 Produtividade

**LibreOffice** — suíte de escritório completa e gratuita:

| Componente | Equivalente |
|---|---|
| **Writer** | Microsoft Word |
| **Calc** | Microsoft Excel |
| **Impress** | Microsoft PowerPoint |
| **Draw** | Microsoft Visio |

### 6.3 Desenvolvimento

- Editores: VS Code, Gedit, Kate, Vim, Emacs
- Compiladores: GCC, Clang
- IDEs: Eclipse, IntelliJ IDEA, NetBeans

### 6.4 Multimídia e Gráficos

| Categoria | Aplicações |
|---|---|
| Áudio | Rhythmbox, Audacity, VLC |
| Vídeo | VLC, MPV, Kdenlive |
| Imagem | **GIMP** (equivalente ao Photoshop), Inkscape |

> 🎨 O **GIMP** (GNU Image Manipulation Program) é o editor de imagens mais poderoso disponível no Linux.

---

## Cap. 7 — Operações na Linha de Comando

### 7.1 Navegação

```bash
pwd              # Mostra diretório atual
cd /caminho      # Caminho absoluto (parte da raiz /)
cd caminho       # Caminho relativo (parte do diretório atual)
cd ..            # Sobe um nível
cd ~             # Vai para o diretório home
ls -la           # Lista arquivos com detalhes e ocultos
tree             # Exibe árvore de diretórios
pushd /caminho   # Salva posição atual e vai para /caminho
popd             # Retorna à posição salva
```

### 7.2 Links

| Tipo | Comando | Descrição |
|---|---|---|
| **Hard Link** | `ln arquivo link` | Aponta diretamente para o inode do arquivo |
| **Soft Link** | `ln -s arquivo link` | Aponta para o caminho do arquivo (como atalho) |

### 7.3 Fluxos Padrão e Redirecionamento

```bash
# Fluxos padrão
stdin   (0)  # Entrada padrão
stdout  (1)  # Saída padrão
stderr  (2)  # Saída de erro

# Redirecionamento
comando > arquivo        # Redireciona stdout para arquivo (sobrescreve)
comando >> arquivo       # Acrescenta stdout ao arquivo
comando 2> erros.txt     # Redireciona stderr para arquivo
comando < arquivo        # Usa arquivo como stdin
cmd1 | cmd2              # Pipe: saída de cmd1 vira entrada de cmd2
```

### 7.4 Busca de Arquivos

```bash
locate   nome          # Busca em banco de dados (rápido)
find / -name "*.txt"   # Busca por nome
find / -type d         # Busca por tipo (d=diretório, f=arquivo)
find / -size +100M     # Busca por tamanho
find / -mtime -7       # Modificados nos últimos 7 dias
find / -perm 755       # Busca por permissões
```

### 7.5 Leitura de Arquivos

```bash
cat arquivo      # Exibe conteúdo completo
tac arquivo      # Exibe em ordem inversa (última linha primeiro)
less arquivo     # Paginação interativa (q para sair)
head -n 20 arq   # Exibe primeiras 20 linhas
tail -n 20 arq   # Exibe últimas 20 linhas
tail -f arq      # Acompanha arquivo em tempo real (logs)
```

### 7.6 Gerenciamento de Pacotes

| Família | Alto Nível | Baixo Nível |
|---|---|---|
| Debian/Ubuntu | `apt`, `apt-get` | `dpkg` |
| Red Hat/Fedora | `yum`, `dnf` | `rpm` |
| SUSE/openSUSE | `zypper` | `rpm` |

---

## Cap. 8 — Encontrando Documentação

### 8.1 Man Pages

```bash
man ls              # Documentação do comando ls
man 5 passwd        # Seção 5: formato do arquivo /etc/passwd
man -k palavra      # Busca por palavra-chave em todas as man pages
```

**Seções das Man Pages:**

| Seção | Conteúdo |
|---|---|
| 1 | Comandos de usuário |
| 2 | Chamadas de sistema |
| 3 | Funções de biblioteca C |
| 5 | Formatos de arquivo e convenções |
| 8 | Comandos de administração do sistema |

### 8.2 GNU Info

```bash
info ls             # Documentação detalhada e hiperligada
```

> 📖 O sistema `info` oferece documentação mais detalhada que as man pages, com navegação por nós interconectados usando atalhos de teclado.

### 8.3 Ajuda Rápida e Outros Recursos

```bash
ls --help           # Ajuda rápida do comando
help cd             # Ajuda para comandos internos do shell
```

**Outras fontes:**
- 📁 `/usr/share/doc` — documentação de todos os pacotes instalados
- 🖥️ Documentação gráfica disponível no GNOME Help
- 🌐 Recursos online: wiki.archlinux.org, askubuntu.com, man7.org

---

## Cap. 9 — Processos

### 9.1 Tipos e Atributos de Processos

**Estados de um processo:**

| Estado | Descrição |
|---|---|
| **Running** | Em execução ou pronto para executar |
| **Sleeping** | Aguardando evento ou recurso |
| **Stopped** | Processo pausado (ex: com `Ctrl+Z`) |
| **Zombie** | Terminou mas ainda tem entrada na tabela de processos |

**Atributos principais:** PID (Process ID), PPID (Parent PID), UID, GID, prioridade (nice value)

### 9.2 Monitoramento de Processos

```bash
ps aux              # Lista todos os processos em execução
ps -ef              # Formato alternativo completo
pstree              # Exibe processos em árvore hierárquica
top                 # Monitor em tempo real (CPU e memória)
htop                # Versão interativa e colorida do top
```

**Atalhos dentro do `top`:**

| Tecla | Ação |
|---|---|
| `k` | Matar processo (kill) |
| `r` | Mudar prioridade (renice) |
| `q` | Sair |
| `M` | Ordenar por uso de memória |
| `P` | Ordenar por uso de CPU |

### 9.3 Controle de Processos

```bash
comando &           # Executa em background
Ctrl + Z            # Suspende processo atual (coloca em background)
Ctrl + C            # Termina processo atual
jobs                # Lista jobs em background
fg %1               # Traz job 1 para foreground
bg %1               # Retoma job 1 em background
kill PID            # Termina processo pelo PID
kill -9 PID         # Força término imediato (SIGKILL)
```

### 9.4 Agendamento de Processos

```bash
sleep 30            # Pausa por 30 segundos
at 14:30            # Agenda execução única às 14:30
crontab -e          # Edita tarefas agendadas recorrentes
```

**Formato do crontab:**

```
# minuto hora dia mês dia-da-semana comando
  0      2    *   *    *            /backup.sh    # Todo dia às 02:00
  */5    *    *   *    *            /check.sh     # A cada 5 minutos
```

---

## Cap. 10 — Operações com Arquivos

### 10.1 Hierarquia de Diretórios (FHS)

```
/
├── etc/        → Arquivos de configuração do sistema
├── var/        → Dados variáveis (logs, spools, e-mails)
├── home/       → Diretórios pessoais dos usuários
├── bin/        → Executáveis essenciais do sistema
├── usr/bin/    → Executáveis de aplicações de usuário
├── lib/        → Bibliotecas compartilhadas
├── dev/        → Arquivos de dispositivos
├── proc/       → Informações do kernel (sistema de arquivos virtual)
├── sys/        → Interface com o kernel (hardware)
├── tmp/        → Arquivos temporários (limpo no boot)
├── boot/       → Arquivos de boot (kernel, GRUB)
└── mnt/        → Ponto de montagem temporário
```

### 10.2 Montagem de Sistemas de Arquivos

```bash
mount /dev/sdb1 /mnt/disco   # Monta partição
umount /mnt/disco            # Desmonta partição
df -h                        # Exibe espaço em disco (human-readable)
du -sh /caminho              # Tamanho de diretório
```

**Montagem remota via NFS:**

```bash
mount servidor:/compartilhado /mnt/nfs
```

### 10.3 Comparação de Arquivos

```bash
diff arquivo1 arquivo2       # Compara linha a linha
diff -u arq1 arq2            # Formato unificado (mais legível)
file documento.pdf           # Identifica tipo real do arquivo
```

### 10.4 Compressão e Backup

| Ferramenta | Comando | Característica |
|---|---|---|
| **gzip** | `gzip arquivo` | Rápido, boa compressão |
| **bzip2** | `bzip2 arquivo` | Melhor compressão que gzip |
| **xz** | `xz arquivo` | Melhor compressão, mais lento |

**Usando o `tar`:**

```bash
tar -czf backup.tar.gz  /pasta/   # Cria arquivo comprimido com gzip
tar -cjf backup.tar.bz2 /pasta/   # Cria arquivo comprimido com bzip2
tar -xzf backup.tar.gz            # Extrai arquivo gzip
tar -tzf backup.tar.gz            # Lista conteúdo sem extrair
```

---

## Cap. 11 — Editores de Texto

### 11.1 Editores Básicos

**nano** — ideal para iniciantes, atalhos exibidos na tela:

```bash
nano arquivo.txt

# Atalhos principais (^ = Ctrl)
^O    # Salvar (Write Out)
^X    # Sair
^K    # Recortar linha
^U    # Colar linha
^W    # Buscar
```

**gedit** — editor gráfico do GNOME, simples e intuitivo.

### 11.2 Vi / Vim — Modos de Operação

```
┌─────────────────────────────────────────┐
│              MODOS DO VI                │
├───────────┬───────────┬─────────────────┤
│  NORMAL   │  INSERÇÃO │    COMANDO      │
│ (padrão)  │  (edição) │  (: no início) │
├───────────┼───────────┼─────────────────┤
│ navegação │ i, a, o   │ :w  → salvar    │
│ deletar   │ para entrar│ :q  → sair     │
│ copiar    │ ESC p/ sair│ :wq → salvar+sair│
│ colar     │           │ :q! → forçar sair│
└───────────┴───────────┴─────────────────┘
```

**Comandos essenciais do Vi:**

```bash
# Navegação (modo normal)
h j k l     # ← ↓ ↑ →
gg          # Início do arquivo
G           # Fim do arquivo
:n          # Vai para linha n

# Edição
dd          # Apaga linha inteira
yy          # Copia linha (yank)
p           # Cola abaixo
u           # Desfaz (undo)
/palavra    # Busca palavra
```

### 11.3 Emacs

O **Emacs** é altamente extensível, com ecossistema próprio muito além de edição de texto. Usa a tecla `Ctrl` (C-) e `Meta/Alt` (M-):

```bash
C-x C-s     # Salvar
C-x C-c     # Sair
C-s         # Buscar
C-k         # Recortar linha (kill)
C-y         # Colar (yank)
M-x         # Executar comando por nome
```

---

## Cap. 12 — Ambiente do Usuário

### 12.1 Contas e Grupos

**Tipos de conta no Linux:**

| Tipo | Descrição |
|---|---|
| **root** | Superusuário — poderes absolutos no sistema |
| **Usuário Regular** | Conta de uso cotidiano com permissões limitadas |
| **De Sistema** | Usada por serviços do sistema operacional |
| **De Serviço** | Usada por aplicações específicas |

**Arquivo `/etc/passwd`** — formato de cada linha:
```
usuario:x:UID:GID:comentário:/home/usuario:/bin/bash
```

**Scripts de configuração do bash:**

| Arquivo | Quando é executado |
|---|---|
| `~/.bash_profile` | Login interativo |
| `~/.bashrc` | Shell interativo não-login |
| `/etc/profile` | Configurações globais (todos os usuários) |

### 12.2 sudo e su

```bash
sudo comando          # Executa comando com privilégios root
sudo -i               # Abre shell root interativo
su                    # Troca para usuário root (requer senha do root)
su - usuario          # Troca para outro usuário
```

> 🔐 **Boa prática:** prefira sempre `sudo` ao `su`. O `sudo` registra todas as ações em log e não exige a senha do root.

### 12.3 Variáveis de Ambiente

```bash
env                     # Lista todas as variáveis de ambiente
echo $HOME              # Exibe valor de uma variável
export MINHA_VAR=valor  # Define e exporta variável
```

**Variáveis essenciais:**

| Variável | Significado |
|---|---|
| `$HOME` | Diretório pessoal do usuário |
| `$PATH` | Diretórios onde o shell busca executáveis |
| `$PS1` | Formato do prompt do terminal |
| `$SHELL` | Shell padrão do usuário |
| `$USER` | Nome do usuário atual |

### 12.4 Histórico e Aliases

```bash
history               # Lista comandos anteriores
!!                    # Repete último comando
!n                    # Repete comando número n
Ctrl + R              # Busca reversa no histórico

# Criando aliases
alias ll='ls -la'
alias atualizar='sudo apt update && sudo apt upgrade'
```

> 💾 Para tornar aliases permanentes, adicione-os ao arquivo `~/.bashrc`.

### 12.5 Permissões de Arquivo

**Estrutura das permissões:**

```
-rwxr-xr--
│└┬┘└┬┘└┬┘
│ │  │  └── Outros (others): r--  = leitura apenas
│ │  └───── Grupo (group):   r-x  = leitura + execução
│ └──────── Dono (owner):    rwx  = leitura + escrita + execução
└────────── Tipo: - arquivo  d diretório  l link simbólico
```

**Comandos de permissão:**

```bash
chmod 755 arquivo      # Notação octal
chmod u+x arquivo      # Notação simbólica: adiciona execução ao dono
chmod go-w arquivo     # Remove escrita de grupo e outros
chown usuario arquivo  # Altera dono do arquivo
chgrp grupo arquivo    # Altera grupo do arquivo
chown user:group arq   # Altera dono e grupo simultaneamente
```

**Tabela octal de permissões:**

| Octal | Binário | Permissões |
|---|---|---|
| 7 | 111 | rwx |
| 6 | 110 | rw- |
| 5 | 101 | r-x |
| 4 | 100 | r-- |
| 0 | 000 | --- |

---

## Cap. 13 — Manipulação de Texto

### 13.1 cat, tac e echo

```bash
cat arquivo              # Exibe conteúdo
cat arq1 arq2 > novo     # Concatena arquivos
tac arquivo              # Exibe em ordem inversa

echo "Olá"               # Imprime string
echo "texto" > arq.txt   # Cria arquivo com conteúdo
echo "mais" >> arq.txt   # Acrescenta ao arquivo
```

### 13.2 sed — Stream Editor

```bash
sed 's/velho/novo/'      arquivo   # Substitui primeira ocorrência por linha
sed 's/velho/novo/g'     arquivo   # Substitui todas as ocorrências (global)
sed -n '5,10p'           arquivo   # Imprime linhas 5 a 10
sed '/padrão/d'          arquivo   # Deleta linhas com padrão
sed -i 's/foo/bar/g'     arquivo   # Edita o arquivo diretamente (in-place)
```

### 13.3 awk — Processamento de Texto

```bash
awk '{print $1}'         arquivo   # Imprime primeira coluna
awk -F: '{print $1}'    /etc/passwd  # Usa : como separador de campo
awk '/padrão/ {print}'   arquivo   # Imprime linhas com padrão
awk '{sum += $1} END {print sum}' arq  # Soma coluna 1
```

### 13.4 Utilitários de Manipulação

```bash
sort arquivo             # Ordena linhas alfabeticamente
sort -n arquivo          # Ordena numericamente
sort -r arquivo          # Ordena em ordem reversa
uniq arquivo             # Remove linhas duplicadas adjacentes
sort arq | uniq          # Remove todas as duplicatas

paste arq1 arq2          # Une arquivos lado a lado (colunas)
join arq1 arq2           # Une por campo comum (como JOIN no SQL)
split -l 100 arq parte_  # Divide arquivo em partes de 100 linhas
```

### 13.5 grep — Busca de Padrões

```bash
grep "padrão"     arquivo     # Busca padrão em arquivo
grep -r "padrão"  /pasta/     # Busca recursiva em diretório
grep -i "padrão"  arquivo     # Case-insensitive
grep -n "padrão"  arquivo     # Mostra número de linha
grep -v "padrão"  arquivo     # Inverte: mostra linhas SEM o padrão
grep -c "padrão"  arquivo     # Conta ocorrências
grep -E "regex"   arquivo     # Usa expressões regulares estendidas
```

### 13.6 Outros Utilitários de Texto

```bash
tr 'a-z' 'A-Z'           # Converte minúsculas em maiúsculas
tr -d ' '                # Remove espaços

tee arquivo.txt          # Envia saída para arquivo E para stdout

wc arquivo               # Conta linhas, palavras e caracteres
wc -l arquivo            # Conta apenas linhas
wc -w arquivo            # Conta apenas palavras

cut -d: -f1 /etc/passwd  # Extrai campo 1 usando : como delimitador
cut -c1-10 arquivo       # Extrai caracteres 1 a 10 de cada linha

strings binário          # Extrai strings legíveis de arquivo binário
```

---

## Cap. 14 — Operações de Rede

### 14.1 Fundamentos de Rede

**Tipos de endereço IP:**

| Tipo | Formato | Exemplo |
|---|---|---|
| **IPv4** | 4 octetos decimais | `192.168.1.100` |
| **IPv6** | 8 grupos hexadecimais | `fe80::1/64` |

**Comandos de diagnóstico:**

```bash
ifconfig                  # Exibe interfaces de rede (legado)
ip addr                   # Exibe endereços IP (moderno)
ip link                   # Exibe interfaces de rede
ip route                  # Exibe tabela de roteamento

ping google.com           # Testa conectividade (ICMP)
ping -c 4 google.com      # Envia 4 pacotes e para

traceroute google.com     # Rastreia rota até destino
route -n                  # Exibe tabela de roteamento numérica
```

### 14.2 Configuração de Rede

**Arquivos de configuração por família:**

| Família | Arquivo |
|---|---|
| Red Hat / CentOS | `/etc/sysconfig/network-scripts/ifcfg-eth0` |
| Debian / Ubuntu | `/etc/network/interfaces` ou Netplan |
| Todas | `/etc/hosts`, `/etc/resolv.conf` |

```bash
# /etc/hosts — resolução local de nomes
127.0.0.1   localhost
192.168.1.10  servidor-local

# /etc/resolv.conf — servidores DNS
nameserver 8.8.8.8
nameserver 1.1.1.1
```

### 14.3 Transferência de Arquivos

```bash
# wget — download de arquivos
wget https://exemplo.com/arquivo.tar.gz
wget -c url           # Continua download interrompido
wget -r url           # Download recursivo

# curl — transferência multi-protocolo
curl https://api.exemplo.com
curl -O url           # Salva com nome original
curl -o saida.html url # Salva com nome personalizado

# scp — cópia segura via SSH
scp arquivo usuario@servidor:/destino/
scp -r pasta/ usuario@servidor:/destino/

# sftp — FTP seguro interativo
sftp usuario@servidor

# ssh — acesso remoto seguro
ssh usuario@servidor
ssh -p 2222 usuario@servidor   # Porta personalizada
```

### 14.4 Navegadores de Linha de Comando

```bash
lynx https://exemplo.com    # Navegador texto clássico
w3m  https://exemplo.com    # Navegador texto moderno
```

---

## Cap. 15 — Shell Bash e Scripting Básico

### 15.1 Estrutura de um Script

```bash
#!/bin/bash
# Shebang obrigatório na primeira linha

echo "Olá, Mundo!"

# Verificar valor de retorno do último comando
ls /inexistente
echo "Código de saída: $?"   # 0 = sucesso, diferente de 0 = erro
```

```bash
chmod +x script.sh    # Tornar executável
./script.sh           # Executar
```

### 15.2 Variáveis e Parâmetros

```bash
#!/bin/bash

nome="Linux"
echo "Bem-vindo ao $nome"

# Parâmetros posicionais
echo "Script: $0"
echo "1º parâmetro: $1"
echo "2º parâmetro: $2"
echo "Todos: $@"
echo "Quantidade: $#"

# Substituição de comandos
data=$(date)
arquivos=$(ls | wc -l)
echo "Data atual: $data"
echo "Arquivos no diretório: $arquivos"
```

### 15.3 Funções

```bash
#!/bin/bash

saudacao() {
    echo "Olá, $1!"
    return 0
}

saudacao "Maria"
saudacao "João"
```

### 15.4 Estruturas Condicionais

```bash
#!/bin/bash

# if-then-else
if [ $1 -gt 10 ]; then
    echo "Maior que 10"
elif [ $1 -eq 10 ]; then
    echo "Igual a 10"
else
    echo "Menor que 10"
fi

# Testes de arquivo
if [ -f "/etc/passwd" ]; then echo "Arquivo existe"; fi
if [ -d "/home" ];       then echo "É um diretório"; fi
if [ -x "/bin/bash" ];   then echo "É executável"; fi
if [ -r "arq.txt" ];     then echo "Tem leitura"; fi

# Testes de string
if [ -z "$var" ];        then echo "String vazia"; fi
if [ -n "$var" ];        then echo "String não vazia"; fi
if [ "$a" = "$b" ];      then echo "Strings iguais"; fi

# Testes numéricos
[ $a -eq $b ]   # igual
[ $a -ne $b ]   # diferente
[ $a -gt $b ]   # maior que
[ $a -lt $b ]   # menor que
[ $a -ge $b ]   # maior ou igual
[ $a -le $b ]   # menor ou igual
```

### 15.5 Aritmética

```bash
x=10
y=3

echo $((x + y))     # 13
echo $((x - y))     # 7
echo $((x * y))     # 30
echo $((x / y))     # 3
echo $((x % y))     # 1 (módulo)
echo $((x ** y))    # 1000 (potência)

let resultado=x+y
echo $resultado
```

---

## Cap. 16 — Bash Shell Scripting Avançado

### 16.1 Manipulação de Strings

```bash
str="Hello World"

echo ${#str}           # Comprimento: 11
echo ${str:6}          # Substring a partir do índice 6: World
echo ${str:0:5}        # Substring do índice 0 com 5 chars: Hello
echo ${str,,}          # Converte para minúsculas: hello world
echo ${str^^}          # Converte para maiúsculas: HELLO WORLD
echo ${str/World/Linux} # Substitui: Hello Linux
```

### 16.2 Expressões Booleanas

```bash
# AND: ambas as condições verdadeiras
if [ $a -gt 0 ] && [ $b -gt 0 ]; then echo "Ambos positivos"; fi

# OR: pelo menos uma condição verdadeira
if [ $a -gt 0 ] || [ $b -gt 0 ]; then echo "Pelo menos um positivo"; fi

# NOT: inverte condição
if [ ! -f "arquivo" ]; then echo "Arquivo não existe"; fi
```

### 16.3 Comando case

```bash
#!/bin/bash
# Ideal para tratar opções de linha de comando

case "$1" in
    start)
        echo "Iniciando serviço..."
        ;;
    stop)
        echo "Parando serviço..."
        ;;
    restart)
        echo "Reiniciando serviço..."
        ;;
    *)
        echo "Uso: $0 {start|stop|restart}"
        exit 1
        ;;
esac
```

### 16.4 Loops

```bash
# FOR — itera sobre lista
for i in 1 2 3 4 5; do
    echo "Item: $i"
done

for arquivo in *.txt; do
    echo "Processando: $arquivo"
done

for ((i=0; i<10; i++)); do
    echo $i
done

# WHILE — repete enquanto condição for verdadeira
contador=0
while [ $contador -lt 5 ]; do
    echo "Contador: $contador"
    ((contador++))
done

# UNTIL — repete até condição se tornar verdadeira
n=1
until [ $n -gt 5 ]; do
    echo "n = $n"
    ((n++))
done
```

### 16.5 Depuração de Scripts

```bash
#!/bin/bash
set -x          # Habilita modo debug (mostra cada comando)
set -e          # Para execução se qualquer comando falhar
set -u          # Trata variáveis não definidas como erro

# ... código ...

set +x          # Desabilita modo debug

# Redirecionar erros para arquivo
./script.sh 2> erros.log
```

### 16.6 Técnicas Extras

```bash
# Arquivos temporários (nome único automático)
tmpfile=$(mktemp)
tmpdir=$(mktemp -d)
echo "Arquivo temporário: $tmpfile"

# Descartar saída indesejada
comando > /dev/null 2>&1

# Números aleatórios
echo $RANDOM                   # Número entre 0 e 32767
echo $((RANDOM % 100))         # Número entre 0 e 99
```

---

## Cap. 17 — Impressão

### 17.1 CUPS — Common Unix Printing System

O **CUPS** é o sistema de impressão padrão no Linux moderno.

**Componentes do CUPS:**
- Scheduler (agendador de impressão)
- Filter system (converte formatos)
- Backend (comunica com impressoras)
- Interface web: `http://localhost:631`

```bash
# Gerenciamento do serviço CUPS
systemctl start   cups
systemctl enable  cups
systemctl status  cups
```

**Configuração de impressoras:**
- 🖥️ Via interface gráfica: Configurações → Impressoras
- 🌐 Via interface web: `http://localhost:631`
- 💻 Via linha de comando: `lpadmin`

### 17.2 Impressão pela Linha de Comando

```bash
lp arquivo.pdf                   # Imprime arquivo
lp -n 3 arquivo.pdf              # Imprime 3 cópias
lp -d impressora arquivo.pdf     # Imprime em impressora específica
lpr arquivo.txt                  # Alternativa ao lp

lpq                              # Lista fila de impressão
lpq -P impressora                # Fila de impressora específica
lprm job_id                      # Remove trabalho da fila
cancel job_id                    # Cancela trabalho de impressão

lpstat -p                        # Lista impressoras disponíveis
lpstat -t                        # Status completo do sistema de impressão
```

### 17.3 Manipulação de PDF e PostScript

```bash
# enscript — converte texto para PostScript
enscript -p saida.ps entrada.txt
enscript --landscape -p saida.ps arq.txt   # Modo paisagem

# pdftk — manipulação de PDFs
pdftk arq1.pdf arq2.pdf cat output merged.pdf   # Mesclar PDFs
pdftk entrada.pdf burst                          # Dividir em páginas
pdftk entrada.pdf encrypt_128bit               \
      owner_pw DONO user_pw USUARIO            \
      output protegido.pdf                       # Criptografar

# Conversão PDF ↔ PostScript
pdf2ps  entrada.pdf  saida.ps     # PDF para PostScript
ps2pdf  entrada.ps   saida.pdf    # PostScript para PDF
```

---

## Cap. 18 — Princípios de Segurança Local

### 18.1 Tipos de Conta e Root

| Conta | Descrição | UID |
|---|---|---|
| **root** | Superusuário — acesso irrestrito | 0 |
| **Usuário Regular** | Conta de uso diário | 1000+ |
| **De Sistema** | Usada por serviços do SO | 1-999 |
| **De Serviço** | Usada por aplicações | variável |

**Operações que requerem root:**
- Instalar/remover pacotes de sistema
- Criar/gerenciar contas de usuário
- Configurar interfaces de rede
- Modificar arquivos em `/etc`, `/bin`, `/usr`
- Montar/desmontar sistemas de arquivos

**Operações que NÃO requerem root:**
- Gerenciar arquivos em `/home/usuario`
- Instalar software no diretório pessoal
- Configurar preferências de desktop
- Usar navegador, editores, aplicações de usuário

### 18.2 sudo vs su

```bash
# sudo — executa UM comando com privilégios elevados
sudo apt update                   # Executa como root
sudo -u outro_user comando        # Executa como outro usuário
sudo -i                           # Shell root interativo

# su — TROCA de identidade
su                                # Torna-se root (requer senha do root)
su - usuario                      # Torna-se outro usuário (shell de login)
su -c "comando" usuario           # Executa comando como usuário
```

> ✅ **Prefira sempre `sudo`:** registra ações em log, não requer senha do root, e limita o escopo do acesso privilegiado.

### 18.3 Isolamento de Processos e Hardware

- Cada processo tem seu **próprio espaço de memória** — processos não acessam memória uns dos outros
- Permissões de acesso a dispositivos são controladas por arquivos em `/dev`
- Manter o sistema **atualizado** é a medida de segurança mais importante e eficaz

```bash
# Atualização do sistema
sudo apt update && sudo apt upgrade          # Debian/Ubuntu
sudo dnf update                              # Fedora/RHEL
sudo zypper update                           # openSUSE
```

### 18.4 Senhas e Armazenamento Seguro

**Armazenamento de senhas:**

| Arquivo | Conteúdo |
|---|---|
| `/etc/passwd` | Informações de conta (sem senha real) |
| `/etc/shadow` | Senhas com hash criptográfico (root only) |

```bash
# Formato de /etc/shadow
usuario:$6$salt$hash:18000:0:99999:7:::
         │─────────── hash SHA-512
```

**Boas práticas de senha:**
- ✅ Mínimo de 12 caracteres
- ✅ Combinação de maiúsculas, minúsculas, números e símbolos
- ✅ Não reutilizar senhas
- ✅ Usar gerenciador de senhas
- ❌ Nunca usar dados pessoais (nome, data de nascimento)
- ❌ Nunca compartilhar senhas

**Ferramentas de política de senhas:**
```bash
chage -l usuario         # Exibe informações de validade da senha
chage -M 90 usuario      # Define validade máxima de 90 dias
passwd usuario           # Altera senha de um usuário
```

### 18.5 Segurança do Boot

**Proteger o GRUB com senha:**

```bash
# Gerar hash da senha
grub2-mkpasswd-pbkdf2

# Adicionar ao /etc/grub.d/40_custom:
set superusers="admin"
password_pbkdf2 admin grub.pbkdf2.sha512.10000.HASH...
```

**Proteção de hardware:**
- 🔒 Configurar BIOS/UEFI para solicitar senha no boot
- 🔒 Desabilitar boot por USB/CD na BIOS
- 🔒 Habilitar Secure Boot (UEFI)
- 🔒 Usar criptografia de disco completo (LUKS)

```bash
# Verificar status do Secure Boot
mokutil --sb-state
```

---

## Recursos Úteis

### 📚 Documentação Oficial

- [Linux Foundation Training](https://training.linuxfoundation.org) — Cursos e certificações oficiais
- [The Linux Documentation Project](https://tldp.org) — Guias e HOWTOs extensos
- [man7.org](https://man7.org/linux/man-pages/) — Man pages online

### 🎓 Certificações Linux Foundation

| Certificação | Nível |
|---|---|
| **LFCS** — Linux Foundation Certified SysAdmin | Intermediário |
| **LFCE** — Linux Foundation Certified Engineer | Avançado |
| **CKA** — Certified Kubernetes Administrator | Avançado |

### 🌐 Comunidades e Fóruns

- [Ask Ubuntu](https://askubuntu.com) — Fórum da comunidade Ubuntu
- [Stack Overflow (Linux)](https://stackoverflow.com/questions/tagged/linux)
- [Reddit r/linux](https://reddit.com/r/linux) e [r/linuxquestions](https://reddit.com/r/linuxquestions)
- [Arch Linux Wiki](https://wiki.archlinux.org) — Referência técnica detalhada

### 🛠️ Ferramentas Online

- [ExplainShell](https://explainshell.com) — Explica qualquer comando bash
- [Regex101](https://regex101.com) — Testador de expressões regulares
- [Crontab Guru](https://crontab.guru) — Gerador visual de expressões cron
- [ShellCheck](https://shellcheck.net) — Verificador de scripts bash

---

> 📌 **Sobre o Curso:** O LFS101 da Linux Foundation é uma formação completa de **40 a 60 horas**, inteiramente autodirigida, que parte do zero e constrói progressivamente todo o conhecimento necessário para operar um sistema Linux com autonomia — cobrindo desde filosofia e boot até segurança, scripting, redes e impressão.

---
*Resumo baseado no curso LFS101 — Introduction to Linux | Linux Foundation*
