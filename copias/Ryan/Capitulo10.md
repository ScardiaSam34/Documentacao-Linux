    # 🔹 Capítulo 10 – File Operations

    ## 🔹 Tópicos
    - Filesystems (Sistemas de Arquivos)
    - Filesystem Layout (Layout do Sistema de Arquivos)
    - Comparando Arquivos e Tipos de Arquivos
    - Fazendo Backup e Compactando Dados
    - Editores de Texto: Vim e Emacs (Adicional)
    - Shell, Ambiente e Histórico de Comandos (Adicional)
    - Usuários, Privilégios e Permissões (Adicional)

    ---

    ## 🔹 Subtópicos

    ### Filesystems (Sistemas de Arquivos e Partições)
    Um sistema de arquivos (filesystem) é a estrutura lógica que o sistema operacional usa para organizar, armazenar e recuperar dados em um disco.
    As **partições** ajudam a segregar arquivos de acordo com o uso, propriedade e tipo, dividindo o disco físico em seções lógicas independentes (por exemplo, separar os arquivos do sistema dos arquivos dos usuários). 

    ### Mount Points, Mounting e NFS
    A árvore do sistema de arquivos no Linux é única e começa no diretório raiz (`/`). Qualquer partição, disco ou dispositivo de armazenamento extra deve ser "anexado" a essa árvore em um diretório vazio chamado **Mount Point** (ponto de montagem).
    - **Mounting/Unmounting:** É o processo de conectar (mount) ou desconectar (umount) esses dispositivos da árvore. A montagem automática durante a inicialização do sistema é configurada editando o arquivo `/etc/fstab`.
    - **NFS (Network File System):** É um protocolo de rede que permite a um servidor compartilhar seus diretórios e arquivos com clientes através da rede, de forma que os clientes possam "montar" esses diretórios remotos como se fossem discos locais.

    ---

    ### Filesystem Layout (FHS)

    O Linux segue o **Filesystem Hierarchy Standard (FHS)**, um padrão que define a estrutura de diretórios do sistema. A árvore começa no diretório raiz, representado por `/`. Principais diretórios:
    - **`/home` e `/root`:** O `/home` contém os diretórios pessoais dos usuários comuns. O `/root` (slash-root) é o diretório pessoal exclusivo do administrador (usuário root).
    - **`/bin` e `/sbin`:** Contêm os comandos e programas binários executáveis. O `/bin` é para uso geral, enquanto o `/sbin` contém ferramentas de administração do sistema (System Binaries).
    - **`/proc`:** É um "pseudo-filesystem". Ele não existe no disco rígido, mas sim na memória RAM, fornecendo informações em tempo real sobre o kernel, hardware e processos em execução.
    - **`/dev`:** Contém arquivos de dispositivos (devices), representando o hardware do sistema (discos, terminais, etc.).
    - **`/var`:** Armazena dados variáveis que crescem e mudam constantemente, como logs do sistema e spools de impressão. Frequentemente é colocado em uma partição separada para que seu crescimento não lote o disco principal e afete o sistema.
    - **`/etc`:** Contém os arquivos de configuração locais do sistema e dos aplicativos.
    - **`/boot`:** Contém os arquivos fundamentais necessários para inicializar o sistema (como o kernel do Linux e o bootloader).
    - **`/lib` e `/lib64`:** Armazenam bibliotecas compartilhadas essenciais necessárias pelos binários no `/bin` e `/sbin`.
    - **`/media`, `/run` e `/mnt`:** Usados para mídias removíveis. O `/mnt` é tradicionalmente usado para montagens manuais temporárias, enquanto o `/media` e `/run` lidam com montagens automáticas (como pendrives USB).
    - **`/usr`:** Contém a maior parte dos programas, bibliotecas e documentações instaladas para os usuários.

    ---

    ### Comparando Arquivos e Tipos de Arquivos
    No Linux, **a extensão de um arquivo (.txt, .mp3, .sh) não define o seu tipo**. O sistema verifica o conteúdo e os cabeçalhos internos do arquivo para descobrir o que ele é.
    - O utilitário **`file`** é usado exatamente para analisar e relatar de forma precisa o verdadeiro tipo de um arquivo.
    - Para verificar modificações em textos ou códigos fonte, as ferramentas **`diff`** e **`diff3`** comparam arquivos e exibem as diferenças exatas (deltas) entre eles. A ferramenta **`patch`** pega essas diferenças e as aplica a um arquivo original para atualizá-lo para uma nova versão de forma automatizada.

    ---

    ### Fazendo Backup e Compactando Dados
    O gerenciamento de dados envolve arquivar (juntar vários arquivos em um só) e compactar (reduzir o tamanho).
    - **`cp` vs `rsync`:** O `cp` copia arquivos localmente. O `rsync` é mais avançado: ele pode copiar arquivos de uma máquina para outra pela rede e sincronizar diretórios, transferindo apenas os pedaços de arquivos que foram modificados, economizando muito tempo e banda.
    - **Arquivamento com `tar`:** A ferramenta `tar` agrupa vários arquivos e diretórios em um único arquivo de saída, frequentemente chamado de *tarball*. 
    - **Compactação:** Ferramentas como **`gzip`**, **`bzip2`**, **`xz`** e **`zip`** são usadas para diminuir o tamanho dos arquivos. Elas diferem no tempo de processamento e na taxa de compactação (por exemplo, o `xz` demora mais para compactar, mas gera arquivos muito menores). O `tar` pode invocar essas ferramentas automaticamente ao criar o arquivo.
    - **Cópias bit a bit:** A ferramenta **`dd`** realiza cópias em nível de bloco (disk-to-disk). Ela cria cópias exatas e idênticas, sendo capaz de clonar partições ou discos inteiros com alta eficiência.

    ---

    ### Editores de Texto: Vim e Emacs (Conteúdo Adicional)
    Administrar um sistema Linux requer habilidade com editores de texto via terminal. 
    - **Vim:** Um dos editores mais populares. Para iniciantes que desejam iniciar o tutorial interativo do Vim e aprender seus comandos básicos, basta usar o comando `vimtutor`.
    - **Emacs:** Outro editor extremamente poderoso e extensível. Para sair (exit) do Emacs, após ele solicitar que você salve todos os arquivos modificados, o atalho correto é `CTRL-x CTRL-c`.

    ---

    ### Shell, Ambiente e Histórico de Comandos (Conteúdo Adicional)
    O ambiente do usuário no Linux pode ser amplamente customizado, o que traz mais produtividade.
    - **Startup Files (Arquivos de Inicialização):** Arquivos como `~/.bashrc` ou `~/.bash_profile` são lidos quando o shell inicia. As grandes vantagens desses arquivos de inicialização são que eles **podem definir atalhos e aliases de linha de comando** e **configurar o editor de texto padrão** do sistema.
    - **Variáveis de Ambiente:** Armazenam configurações do sistema usadas pelo shell e por programas. Uma das mais comumente usadas é a variável `HOME`, que define o diretório pessoal do usuário. Outra variável fundamental é a `PS1`, que é usada para **especificar a string do prompt** do terminal. Por exemplo, para configurar seu prompt do bash para incluir o diretório de trabalho atual (current working directory), você deve usar:
    ```
    export PS1='\w$ '
    ```
    - **Criando Aliases:** Você pode criar apelidos para comandos longos. Para criar um alias chamado `cdtmp` que executa `cd /tmp`, a sintaxe correta (sem espaços ao redor do sinal de igual) é:
    ```
    alias cdtmp='cd /tmp'
    ```
    - **Histórico de Comandos (History):** O shell armazena os comandos digitados anteriormente em um arquivo oculto no diretório do usuário: `~/.bash_history`. Para encontrar facilmente e reexecutar um comando usado anteriormente, a forma mais prática é **pressionar a seta para cima (Up arrow key)** até localizá-lo e então apertar Enter. Se você souber o número do comando no histórico (por exemplo, o comando 70), você pode executá-lo em apenas um passo digitando:
    ```
    !70
    ```

    ---

    ### Usuários, Privilégios e Permissões (Conteúdo Adicional)
    A segurança no Linux é baseada na separação estrita de privilégios entre os usuários e o administrador (root).
    - **Contas de Usuário (UserIDs):** O sistema identifica os usuários numericamente através dos UIDs (User IDs). Em sistemas Linux modernos, as contas de usuários comuns (Normal userids) possuem **valores de 1000 ou maiores**.
    - **Privilégios (su vs sudo):** Ao realizar tarefas administrativas, a regra de ouro é que **o comando `sudo` é mais seguro de usar do que o comando `su`**. O `sudo` permite que usuários executem comandos com privilégios de root fornecendo suas próprias senhas (e mantém um registro de auditoria do que foi feito), enquanto o `su` exige o compartilhamento da senha direta do root.
    - **Permissões Básicas:** A visualização de permissões de um arquivo no Linux segue a estrutura Read (r), Write (w) e Execute (x). Uma permissão que fornece **acesso de leitura e execução**, mas sem permissão de escrita, é representada como `r-x`.

    ---

    # 🔹 Conteúdo

    Neste capítulo, mergulhei profundamente nas operações de arquivos e na estrutura do Linux. Aprendi que tudo no sistema de arquivos começa no diretório raiz (`/`) e que o Linux segue o padrão FHS (Filesystem Hierarchy Standard), o que torna a localização de arquivos previsível. Entendi a função de diretórios cruciais: o `/boot` para inicialização, o `/etc` para configurações, o `/var` para logs que crescem com o tempo, e o `/proc`, que é um sistema de arquivos virtual rodando direto na memória RAM.

    Entendi o conceito de partições e como separar os dados é uma boa prática de segurança e performance. Aprendi que novos discos e partições não aparecem magicamente como "Unidade D:", mas precisam ser montados em "Mount Points" (diretórios vazios) na árvore principal, e que o arquivo `/etc/fstab` controla a montagem automática no boot. Também vi como o protocolo NFS permite montar sistemas de arquivos pela rede.

    Outra quebra de paradigma foi entender que o Linux não depende de extensões para saber o que um arquivo é; aprendi a usar o comando `file` para descobrir a real natureza dos dados. Para gerenciar versões de arquivos de configuração ou código, aprendi a identificar as diferenças com o comando `diff` e a aplicar atualizações automaticamente usando o comando `patch`.

    Explorei as ferramentas essenciais para backup e transferência de dados. Descobri que enquanto o `cp` faz cópias básicas locais, o `rsync` é a ferramenta definitiva para sincronizar dados até mesmo entre máquinas diferentes. Para reduzir o uso de disco, aprendi a agrupar diretórios inteiros em *tarballs* usando o comando `tar` e a compactá-los usando algoritmos como `gzip`, `bzip2`, `xz` e `zip`. Para cenários de clonagem de discos inteiros e partições, aprendi sobre o comando `dd`, que faz cópias exatas em nível de bloco físico.

    Para fechar minha imersão em gerenciamento prático, estudei o uso de editores essenciais, descobrindo o comando `vimtutor` para treinar no Vim e a combinação `CTRL-x CTRL-c` para sair do Emacs. Compreendi as fundações do shell, configurando variáveis de ambiente como a `HOME` e a `PS1` (incluindo o caminho atual usando `\w$`), gerenciando meus atalhos e aliases via arquivos de inicialização, e dominando o histórico com a tecla *Up arrow* e a sintaxe `!numero` vinculada ao arquivo `~/.bash_history`. Por fim, consolidei a segurança básica: IDs de usuários comuns começando em 1000, as permissões representadas simbolicamente (como `r-x` para ler e executar) e a superioridade de segurança do comando `sudo` em relação ao antigo comando `su`.

    ---

    # Comandos do Capítulo

    | Comando | Descrição |
    |--------|-----------|
    | `mount` | Anexa um sistema de arquivos, partição ou dispositivo de rede à árvore de diretórios do Linux. |
    | `umount` | Desconecta (desmonta) um sistema de arquivos previamente montado. |
    | `diff` | Compara o conteúdo de dois arquivos linha por linha e mostra as diferenças (deltas). |
    | `patch` | Aplica as diferenças geradas pelo `diff` para atualizar um arquivo original. |
    | `file` | Analisa o conteúdo de um arquivo para determinar o seu verdadeiro tipo, ignorando a extensão. |
    | `rsync` | Sincroniza e copia arquivos localmente ou pela rede de forma otimizada (apenas as diferenças). |
    | `tar` | Cria ou extrai arquivos de arquivo morto (*archive*), juntando múltiplos arquivos em um só (*tarball*). |
    | `gzip`, `bzip2`, `xz` | Utilitários de compactação de dados que reduzem o tamanho dos arquivos com diferentes algoritmos. |
    | `zip` | Compacta arquivos e diretórios no formato amplamente compatível `.zip`. |
    | `dd` | Realiza cópias de dados em nível de bloco, clonando partições ou discos inteiros exatamente. |
    | `vimtutor` | Inicia o tutorial oficial e interativo para aprender os comandos básicos do editor Vim. |
    | `alias` | Permite criar atalhos personalizados para comandos no shell. |
    | `history` | Mostra o histórico de comandos digitados na sessão. O arquivo padrão é o `~/.bash_history`. |

    # Explicação detalhada dos Comandos Básicos do Linux

    ## mount / umount
    O **`mount`** é usado para integrar um sistema de arquivos à hierarquia do Linux. Você especifica o dispositivo e o diretório de destino (ponto de montagem). Exemplo: `mount /dev/sdb1 /mnt/usb`.
    O **`umount`** remove essa integração de forma segura para evitar corrupção de dados. Exemplo: `umount /mnt/usb`. O arquivo `/etc/fstab` atua como o mapa padrão para montagens automáticas ao ligar o PC.

    ## diff e patch
    O **`diff`** lê dois arquivos e exibe as instruções exatas de quais linhas foram adicionadas, removidas ou alteradas para que o primeiro arquivo fique idêntico ao segundo. 
    O **`patch`** pega essa saída (chamada de arquivo de patch) e automatiza o processo de edição. É extremamente usado por desenvolvedores de software e administradores para distribuir atualizações de código ou configurações sem precisar enviar o arquivo inteiro.

    ## file
    Como o Linux não se importa se um script bash termina em `.txt` ou `.sh`, o utilitário **`file`** lê os "magic numbers" (assinaturas no cabeçalho interno do arquivo) e informa se é um executável, uma imagem JPEG, um documento de texto ASCII, etc. Exemplo: `file relatorio` pode retornar "PDF document, version 1.4".

    ## rsync
    Muito superior ao comando `cp` tradicional para backups. O **`rsync`** (Remote Sync) analisa a origem e o destino antes de transferir. Se um arquivo de 1GB teve apenas 10MB alterados, o `rsync` transfere apenas esses 10MB, economizando banda e tempo. Ele pode trabalhar localmente ou via SSH para servidores remotos.

    ## tar
    O **`tar`** (Tape Archive) foi originalmente criado para gravar em fitas magnéticas, mas hoje é o padrão para empacotar dados. Ele não compacta o tamanho por si só, apenas junta milhares de arquivos em um único pacote `.tar`. Contudo, ele aceita *flags* para compactar simultaneamente:
    - `tar -czvf` (cria um arquivo usando `gzip` e gera a extensão `.tar.gz`).
    - `tar -xzvf` (extrai o conteúdo de um arquivo `.tar.gz`).

    ## gzip, bzip2 e xz
    São as ferramentas dedicadas exclusivamente à compactação matemática dos dados.
    - **`gzip`:** O mais rápido e padrão, extensão `.gz`.
    - **`bzip2`:** Mais lento que o gzip, mas entrega arquivos um pouco menores, extensão `.bz2`.
    - **`xz`:** O mais lento para compactar e exige mais memória, mas oferece as melhores taxas de compactação de todas, extensão `.xz`.

    ## dd
    O **`dd`** (Dataset Definition, frequentemente apelidado de "Disk Destroyer" por sua capacidade de apagar discos se usado incorretamente) não entende de arquivos ou diretórios. Ele lê bytes brutos de uma entrada e os copia para uma saída. É ideal para fazer backup exato de um pen drive inteiro (incluindo o setor de boot) ou transferir a imagem de um sistema operacional diretamente para um disco físico (`dd if=/imagem.iso of=/dev/sdc`).

    ---

    ## 🔹 Recursos úteis
    https://linuxcommand.org 
    https://kernel.org 
    https://gnu.org