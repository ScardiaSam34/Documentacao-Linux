# 🐧 LINUX — DOCUMENTAÇÃO COMPLETA (19 CAPÍTULOS)

---

## CAPÍTULO 1 — INTRODUÇÃO AO LINUX
O Linux é um sistema operacional open source baseado no UNIX, criado por Linus Torvalds.

### Características Principais
* **Multiusuário:** Vários usuários podem operar o sistema simultaneamente.
* **Multitarefa:** Capaz de executar múltiplos processos e programas ao mesmo tempo.
* **Seguro:** Sistema robusto de controle de permissões de arquivos e usuários.
* **Estável:** Amplamente utilizado em servidores pela sua alta disponibilidade.

### Estrutura Básica
* **Kernel:** O núcleo do sistema.
* **Ferramentas do Sistema:** Utilitários para administração e uso diário.
* **Interface Gráfica:** Componente opcional para interação visual (GUI).

---

## CAPÍTULO 2 — KERNEL E CONCEITOS FUNDAMENTAIS

### Kernel
O componente central (núcleo) do sistema operacional. É responsável por:
* Gerenciar os recursos de hardware.
* Gerenciar a comunicação entre o hardware e as aplicações (software).

### Desktop Environment (Ambiente de Trabalho)
* Interface gráfica de usuário (GUI) que roda sobre o sistema operacional para facilitar o uso (ex: GNOME).

### Command Line (Linha de Comando)
* A interface (CLI) onde os usuários digitam comandos diretos para o sistema operacional executar.

### Ferramentas de uma Distribuição Completa
Além do kernel, uma distribuição inclui ferramentas para:
* Realizar operações relacionadas a arquivos.
* Prover administração do sistema e gerenciamento de usuários.
* Gerenciar a instalação de pacotes de software.

### Distribuições compatíveis com RHEL (gratuitas)
* CentOS Stream
* AlmaLinux
* Rocky Linux

---

## CAPÍTULO 3 — BOOT E SISTEMA DE ARQUIVOS

### Processo de Boot (x86)
* **BIOS:** Executa o POST (Power-On Self-Test) e inicializa componentes críticos de hardware antes de passar o controle para o bootloader.

### Hierarquia de Diretórios (FHS)
* `/var` → Armazena dados variáveis que mudam constantemente (ex: arquivos de log, filas de impressão).
* `/home` → Diretórios pessoais dos usuários comuns.
* `/root` → Diretório pessoal do superusuário (administrador).

### Conceitos Importantes
* **Case-sensitive:** O Linux difere maiúsculas de minúsculas. `Report.txt` é um arquivo completamente diferente de `report.txt`.
* **Partição x Filesystem:** A partição define os limites físicos do armazenamento (uma área fixa). O filesystem (sistema de arquivos) é a estrutura lógica aplicada nessa área para organizar e recuperar arquivos.
* **Máquinas Virtuais (VMs):** São amplamente recomendadas para aprendizado porque são seguras; falhas na VM não afetam o sistema operacional hospedeiro.

---

## CAPÍTULO 4 — AMBIENTE GRÁFICO E ACESSO

### GNOME
* Um dos ambientes gráficos (Desktop Environment) mais populares no topo do Linux.
* A alteração do papel de parede geralmente é iniciada clicando com o botão direito no desktop e selecionando a opção.

### Ações de Sessão
* **Suspender (Suspend):** Salva o estado atual do sistema na memória RAM para economizar energia.

### Comandos e Utilitários Gráficos (GUI)
* `gnome-tweaks` → Programa que adiciona opções avançadas de personalização ao GNOME, incluindo a instalação de extensões.
* `gedit` → O editor de texto padrão da interface gráfica GNOME.

### Atalhos de Teclado
* **SUPER + L** → Atalho de teclado utilizado para bloquear a tela rapidamente.

### Diretórios Padrão em /home
* Desktop, Documents, Downloads (Root NÃO fica dentro de home).

---

## CAPÍTULO 5 — CONFIGURAÇÕES DO SISTEMA

### Sincronização de Tempo
* **NTP (Network Time Protocol):** Protocolo usado para configurar a hora local sincronizando-a via servidores na internet.

### Configuração de Display
* O painel de Display permite alterar, entre outras coisas, a Screen Resolution (resolução da tela).

### Redes e VPNs
* O utilitário **Network Manager** tem suporte para múltiplas tecnologias VPN (OpenVPN, Cisco OpenConnect, IPSec, etc).

### Comandos e Ferramentas de Pacotes
* `dpkg` → Utilitário de linha de comando de baixo nível usado no Ubuntu/Debian para gerenciar pacotes.
* **Ubuntu Software Center** → Interface gráfica para gerenciamento de software no Ubuntu.
* **YaST software management** → Utilitário utilizado pelo openSUSE para adicionar e remover pacotes.

---

## CAPÍTULO 6 — APLICAÇÕES E DESENVOLVIMENTO

### Email
* **Protocolos:** POP e IMAP (usados para acessar emails em servidores remotos).
* **Comandos CLI (Modo Texto):**
    * `mutt` → Cliente de email de texto, operado via terminal.
    * `mail` → Utilitário básico de linha de comando para enviar e ler emails.
* **Clientes GUI (Gráficos):** Thunderbird e Claws Mail.

### LibreOffice
* **Impress:** Componente do pacote usado para criar e editar apresentações.

### Comandos para Desenvolvedores
* `gcc` → Compilador GNU para a linguagem C e C++.
* `gdb` → O GNU Debugger, usado para depurar programas.
* `git` → Sistema de controle de versão de código-fonte.

---

## CAPÍTULO 7 — COMANDOS ESSENCIAIS DE ARQUIVOS E NAVEGAÇÃO

### Terminais Virtuais
* **CTRL + ALT + F4** → Alterna da interface gráfica (GUI) para o terminal virtual de texto 4.

### Caminhos (Paths)
* Caminho absoluto começa na raiz. Ex: `/etc/passwd` ou `//etc/passwd`.

### Navegação e Manipulação (Comandos)
* `cd` → Muda o diretório atual do usuário.
* `sudo systemctl stop gdm` ou `sudo telinit 3` → Desligam a interface gráfica (dependendo da distribuição).
* `halt`, `poweroff`, `shutdown -h now` → Comandos usados pelo root para desligar o sistema sem reiniciar.
* `less` → Visualizador de arquivos de texto em tela cheia que permite rolagem ("scroll-back").
* `rm -rf` → Remove diretórios de forma recursiva e forçada, sem pedir confirmação. Cuidado ao usar!
* `which` → Mostra o caminho absoluto do executável de um comando.
* `whereis` → Mostra a localização do binário, do código-fonte e da página de manual de um comando.
* `locate` → Realiza uma busca rápida no banco de dados do sistema por um nome ou parte do nome de um arquivo/caminho.

### Coringas (Wildcards)
* `?` → Caractere curinga no bash usado para substituir/casar com exatamente um único caractere qualquer.

### Gerenciadores de Pacotes
* **Alto nível:** `apt`, `dnf`, `zypper` (resolvem dependências automaticamente).
* **Baixo nível:** `dpkg`, `rpm` (instalam pacotes diretos, mas não baixam dependências).

---

## CAPÍTULO 8 — ENCONTRANDO DOCUMENTAÇÃO NO LINUX

### Fontes de Documentação
* As principais fontes de ajuda e documentação no Linux são: as páginas de manual (`man`), o sistema GNU `info`, o comando e opções de `help`, além de uma rica variedade de documentações online e gráficas.

### Páginas de Manual (The man pages)
* `man` → Utilitário de linha de comando que busca, formata e exibe as páginas de manual.
* **Conteúdo:** Oferece documentação aprofundada sobre programas e outros tópicos vitais do sistema, incluindo arquivos de configuração, chamadas de sistema (system calls), rotinas de biblioteca e o próprio kernel.
* **Estrutura:** O manual é historicamente dividido em capítulos (seções) categóricos, permitindo buscar a mesma palavra em contextos diferentes (ex: o comando `passwd` vs. o arquivo de configuração `/etc/passwd`).

### Sistema GNU Info
* `info` → Comando utilizado para acessar o sistema GNU Info.
* **Características:** Foi criado pelo projeto GNU como seu sistema padrão de documentação. É bastante robusto e seu conteúdo é estruturado em páginas/nós (nodes) interligados, similar à navegação por hiperlinks na web.
* **Acesso:** Pode ser operado via linha de comando, web ou ferramentas gráficas de leitura.

### A Opção --help e o Comando help
* `--help` ou `-h` → Opções/argumentos anexados a um comando no terminal para exibir rapidamente uma descrição curta e instruções de uso sem sair da tela atual.
* `help` → Comando direto digitado na linha de comando para exibir a sinopse e detalhes exclusivos de comandos embutidos (built-in commands) do próprio shell.

### Outras Fontes de Documentação
* **Documentação de Pacotes:** Arquivos de texto, licenças e "readmes" que geralmente são instalados localmente no sistema junto com os pacotes de software (frequentemente em `/usr/share/doc`).
* **Sistemas de Ajuda Gráficos:** Interfaces visuais de ajuda (Help) integradas aos ambientes desktop (como GNOME ou KDE).
* **Recursos Online:** A vasta comunidade na Internet, incluindo wikis oficiais de distribuições, fóruns e repositórios de projetos.

## CAPÍTULO 9 — PROCESSOS

### Tipos de Processos
* **Batch process:** Agendado para rodar e depois desconectado do terminal de interação.
* **Daemons:** Processos de servidor iniciados no boot que ficam em background aguardando requisições para trabalhar.

### Conceitos e Prioridades
* **PID (Process ID):** O identificador numérico único de um processo.
* **Nice Value:** Trabalhos de alta prioridade têm valor "nice" mais baixo (negativos), e os de baixa prioridade têm valor "nice" mais alto.
* **Estados:** Os processos podem estar rodando (Running) ou dormindo/aguardando (Sleeping).

### Comandos de Controle de Processos
* **CTRL + C** → Atalho de teclado para encerrar/terminar um processo que está rodando em primeiro plano (foreground).
* **CTRL + Z** → Atalho para suspender temporariamente um processo em foreground.
* `fg` → Traz um processo suspenso ou rodando em background de volta para o primeiro plano (foreground).
* `jobs` → Lista todos os processos em background ativos na sessão atual do terminal.
* `top` → Exibe estatísticas do sistema e os processos consumindo mais recursos em tempo real (mostra PID, PR, UID, USER, processos parados, processos zumbis, etc).
    * *Nota: Dentro do top, pressionar a tecla A não classifica por consumo.*
* `pstree` → Exibe os processos em um formato de árvore gráfica no terminal, mostrando a relação entre processos pai e filho e também threads em chaves.
* `cron` → Daemon/facilidade usado para agendar a execução de tarefas periódicas/recorrentes no sistema.
* `at` → Utilitário para agendar programas não-interativos para rodar uma única vez em um horário específico.

---

## CAPÍTULO 10 — SISTEMA DE ARQUIVOS AVANÇADO E COMPRESSÃO

### Diretórios e Arquivos de Configuração Importantes
* `/etc/fstab` → Arquivo que configura quais sistemas de arquivos serão montados automaticamente no boot no modo multiusuário.
* `/dev` → Onde se encontram os "device nodes" (arquivos especiais de dispositivos do Linux).

### Comandos de Montagem e Análise de Arquivos
* `mount` → Comando usado para montar arquivos e também para visualizar/inquirir se um filesystem está montado como leitura/escrita ou somente leitura.
* `exportfs` → Exporta um sistema de arquivos via NFS para garantir que os diretórios compartilhados fiquem disponíveis na rede.
* `diff -qr <dir1> <dir2>` → Compara duas árvores de diretórios recursivamente listando apenas arquivos diferentes, novos ou deletados.
* `file <arquivo>` → Inspeciona e mostra qual é o tipo de dado/conteúdo contido no arquivo chamado (ex: ASCII text, executável, imagem).

### Comandos de Backup e Compactação
* `tar zcvf backup.tar.gz ~` → Empacota e compacta (via gzip) a árvore completa do diretório home do usuário logado em um arquivo chamado backup.tar.gz.
* `gzip -r <pasta>` → Compacta individualmente todos os arquivos dentro de uma pasta e de todos os subdiretórios sob ela.
* `gunzip foo` (ou `gzip -d foo`) → Descompactam o arquivo compactado foo. Ambos fazem exatamente a mesma coisa.
* `rsync` → Ferramenta de cópia e sincronização de rede que otimiza o tempo copiando apenas as partes de arquivos e subdiretórios que sofreram alterações.

---

## CAPÍTULO 11 — EDITORES DE TEXTO NO TERMINAL

### vim (Vi IMproved)
* `vimtutor` → Comando que inicia um tutorial prático interno para aprender a usar o editor de texto vim.

### emacs
* **CTRL + X seguido de CTRL + C** → Atalho para fechar o editor emacs, solicitando salvar os arquivos modificados.

---

## CAPÍTULO 12 — USUÁRIOS, PERMISSÕES E AMBIENTE

### Contas e Variáveis
* **UID (User ID):** Contas de usuários normais geralmente possuem UIDs de 1000 ou maiores.
* **HOME:** Variável de ambiente comum que guarda o caminho do diretório pessoal do usuário logado.
* **PS1:** Variável de ambiente que define o texto/formato do prompt de comando primário na tela.
* `sudo` é considerado mais seguro do que `su` pois não exige que a senha do administrador seja compartilhada (usa a própria senha do usuário com permissões elevadas).

### Comandos de Ambiente e Histórico
* `alias cdtmp='cd /tmp'` → Cria um atalho (apelido) temporário para que digitar cdtmp execute o comando de mudança para a pasta temporária.
* `export PS1='\w$ '` → Comando que altera o seu prompt no bash para mostrar apenas o diretório de trabalho atual seguido de $.
* `history` → Exibe o histórico de comandos digitados no terminal. (Estes comandos ficam salvos no arquivo `~/.bash_history`).
* **Seta para cima (Up Arrow)** → Atalho no teclado usado para navegar nos comandos anteriormente digitados para rodá-los novamente sem redigitar.
* `!70` → Atalho usado no prompt para executar diretamente o comando listado no número 70 do seu history.

### Permissões (Formato de Letras)
* **r-x** → Significa permissão de Leitura (Read) e Execução (eXecute), sem permissão de gravação.

---

## CAPÍTULO 13 — PROCESSAMENTO E FILTRAGEM DE TEXTO

### Comandos e Expressões Regulares
* `echo` → Comando frequentemente usado para enviar textos ou valores de variáveis diretamente para a tela ou para arquivos (via redirecionamento).
* `cat file1 file2 file3 > file4` → Concatena o conteúdo do file1, file2 e file3 e joga o resultado para dentro do file4.
* `tail -15 arquivo` ou `tail -n15 arquivo` → Exibe as últimas 15 linhas do final do arquivo especificado.
* `sed -e s/dog/pig/g <arquivo>` → Stream editor usado para substituir (s) todas as ocorrências de "dog" por "pig" globalmente (g) no arquivo e mandar para a tela (stdout). (O separador pode variar).
* `awk -F: '{ print $1 $3 }' arquivo` → Avalia o arquivo usando dois-pontos (:) como delimitador (-F:) e imprime apenas as colunas 1 e 3 de cada linha.
* `paste -d` → Comando usado para mesclar linhas de diferentes arquivos, onde a opção -d especifica o caractere delimitador entre as mesclas.
* `join` → Comando que combina as linhas de dois arquivos diferentes lado a lado, desde que essas linhas compartilhem um campo comum exato no começo.
* `$` → Símbolo de expressão regular (regex) usado para identificar e casar padrões localizados estritamente no final de uma string ou linha.
* `grep [0-5] arquivo` ou `grep [0,1,2,3,4,5] arquivo` → Filtra linhas. Retorna e imprime no terminal todas as linhas que contenham algum número de 0 a 5.
* `grep -v <padrão>` → A flag -v inverte a busca; ele exibe todas as linhas do texto que não contenham o padrão especificado.
* `strings` → Vasculha qualquer arquivo (inclusive binários) e imprime na tela todas as sequências de caracteres legíveis por humanos que encontrar.
* `cut` → Recorta e extrai colunas verticais ou seções de cada linha de um arquivo para manipulação.

---

## CAPÍTULO 14 — COMUNICAÇÃO DE REDE E INTERNET

### Testes e SSH
* **FTP (File Transfer Protocol):** Considerado defasado para os padrões modernos porque transmite senhas e dados em texto puro, sem criptografia, podendo ser interceptado.
* `ping` → Envia pacotes ICMP para um destino para verificar se o host remoto está online e se a rede está operante.
* `ssh -l user host` (ou `ssh user@host`) → Estabelece uma conexão remota segura e criptografada a uma máquina remota.

### Navegadores Gráficos
* Mozilla Firefox, Konqueror, Google Chrome.

### Comandos de Download
* `wget` → Utilitário CLI (não interativo) capaz de baixar arquivos ou páginas web a partir da internet.
* `curl` → Outra ferramenta de linha de comando poderosa usada para transferir dados de e para um servidor.

---

## CAPÍTULO 15 — BASH SCRIPTING BÁSICO

### Criação e Execução
* `chmod +x script.sh` → Adiciona a permissão de Execução ao arquivo, transformando um simples texto em um programa rodável.
* `bash script.sh` → Passa o arquivo manualmente e diretamente para o interpretador bash processar e rodar o código.
* `\` **(Barra invertida)** → Usada no fim de uma linha para escapar a quebra de linha, permitindo continuar a digitação do mesmo comando na linha seguinte.
* Um script em bash pode executar aplicações compiladas, comandos internos do bash (built-ins) e invocar outros scripts.

### Variáveis e Expressões
* `$0` → Variável especial contida dentro do script que armazena o nome exato com que o script foi chamado/executado.
* `expr 2 + 3` ou `let x=( 1 + 2 ); echo $x` → Formas válidas de realizar e imprimir adições matemáticas no terminal.

### Operadores e Condicionais
* **Substituição de comando:** `cd $(echo /tmp)` ou ``cd `echo /tmp` `` → Executa o comando em parênteses primeiro e usa o seu resultado (a string "/tmp") como argumento para o comando externo (cd).
* `>` e `>>` → Redirecionadores. `free > /tmp/free.out` sobrescreve o arquivo com o output. `free >> /tmp/free.out` anexa o output no fim do arquivo.
* `if [ $STR1 == $STR2 ]` ou `if [[ $STR1 = $STR2 ]]` → Instruções condicionais no bash para verificar se duas strings de texto são iguais.
* `!` **(Ponto de Exclamação)** → O operador lógico NOT no Bash, usado para inverter uma condição.
* `-e` → Opção usada no "if" para checar se um arquivo ou diretório Existe.
* `-d` → Opção usada no "if" para testar e validar se um caminho específico existe e se ele é um Diretório.

---

## CAPÍTULO 16 — SCRIPTING AVANÇADO E DISPOSITIVOS ESPECIAIS

### Expansão de Variáveis e Loops
* `${#abc}` → Sintaxe especial para retornar o comprimento (número de caracteres) contido na variável abc.
* `case` → Estrutura condicional excelente para testar uma única variável contra vários valores diferentes.
* `for ( j < 10 )` → Uma construção do estilo linguagem C que é inválida se não estiver cercada por `(( ))` adequados no bash. As corretas são `while`, `until` e `for...in`.

### Comandos de Debugging e Logs
* `./script 2>> /tmp/scriptlogfile` → Executa o script e redireciona (usando `2>>`) apenas as saídas de Erro Padrão (stderr) para serem anexadas ao final de um arquivo de log, sem tocar nas saídas corretas.
* `set -x` → Comando inserido no script para ATIVAR o rastreamento (debugging), mostrando na tela tudo que o bash está processando antes de rodar.
* `set +x` → Comando usado para DESATIVAR o rastreamento de debug a partir daquela linha.

### Ferramentas e Dispositivos
* `mktemp -d` → Comando utilizado em scripts para criar pastas/diretórios temporários seguros com nomes aleatórios.
* `/dev/null` → Conhecido como "Bit Bucket" ou buraco negro. Qualquer saída redirecionada para cá desaparece e é descartada.
* `/dev/urandom` e `/dev/random` → "Device nodes" especiais do Linux usados pelo sistema para gerar números aleatórios.

---

## CAPÍTULO 17 — IMPRESSÃO

### CUPS (Common UNIX Printing System)
* Sistema encarregado de conectar impressoras locais e de rede a um sistema Linux e compartilhá-las.

### Comandos de Impressão e PDF
* `lpoptions -d <impressora>` → Comando usado para definir a impressora padrão do sistema.
* `pdftk` e `qpdf` → Utilitários de linha de comando poderosos usados para manipular arquivos PDF.

---

## CAPÍTULO 18 — SEGURANÇA BÁSICA E GERENCIAMENTO DE SENHAS

### Root e Permissões
* **root:** A conta de usuário administrador, que possui autoridade suprema no sistema operacional.
* **Ações que NÃO exigem root:** Acessar arquivos pessoais e mandar arquivos para impressão. Modificar arquivos do sistema requer root.
* **Riscos físicos:** Se a máquina for acessível fisicamente por atacantes, ela está vulnerável a key logging, network sniffing (interceptação de rede) e adulteração do disco.

### Monitoramento e Comandos de Segurança
* `last` → Utilitário que mostra o histórico de sessões logadas, ajudando a identificar há quanto tempo uma conta está inativa.
* `/var/log/auth.log` → Arquivo específico na família Debian (Ubuntu) onde ficam registrados todos os acessos sudo e falhas de login.
* `/etc/shadow` → O arquivo criptografado e super protegido onde as senhas reais ("Shadow passwords") do sistema são armazenadas em distros modernas.
* `chage` → Comando e utilitário Linux usado para configurar o tempo de vida/expiração ("aging") de uma senha.
* **PAM (Pluggable Authentication Modules):** Mecanismo automático em background que, entre outras funções, analisa e rejeita senhas se elas forem consideradas fracas durante o processo de criação.

---

## CAPÍTULO 19 — REVISÃO FINAL
> **Nota:** Este é o compilado consolidado dos conceitos para conclusão do treinamento de introdução ao Linux LFS101.

### Destaques Finais
* O kernel atua diretamente na gerência do hardware.
* A escolha entre `su` e `sudo` pende para o `sudo` por motivos de segurança e auditoria (logs individuais).
* Estruturas de comando em CLI agilizam rotinas administrativas muito mais do que interfaces gráficas (GUI).