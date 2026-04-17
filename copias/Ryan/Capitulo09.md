# Capítulo 9 – Processes, Filesystems & Archiving

    ## Tópicos
    - Introdução a Processos e Atributos de Processo
    - Métricas de Processos e Controle de Processos
    - Listando Processos: ps e top
    - Iniciando Processos no Futuro
    - Sistema de Arquivos, Comparação e Arquivamento (Novo)

    ---

    ## Subtópicos

    ### Introdução a Processos e Atributos (What Is a Process?)
    Um processo é, em essência, um programa em execução. Quando você digita um comando ou inicia um aplicativo, o sistema operacional carrega o código na memória e cria um processo para realizar essa tarefa. Eles podem ser:

    - **Single-threaded:** Possuem apenas uma única linha de execução (fazem uma coisa por vez).
    - **Multi-threaded:** Possuem múltiplas linhas de execução rodando simultaneamente dentro do mesmo processo, dividindo a carga de trabalho e compartilhando os mesmos recursos de memória.

    ---

    ### Tipos de Processos
    Os processos no Linux operam de diferentes formas e dividem-se principalmente em:

    - **Interativos (Interactive):** São processos iniciados por um usuário através de uma sessão de terminal. Eles aguardam a entrada de dados do usuário e enviam a saída de volta para a tela.
    - **Não-interativos (Non-interactive / Daemons):** São processos de sistema ou serviços que rodam silenciosamente em segundo plano, sem estarem anexados a um terminal e sem necessidade de interação humana (ex: um servidor web ou um gerenciador de rede).

    ---

    ### Escalonamento e Estados (Process Scheduling and States)
    Como o Linux é um sistema multitarefa, a CPU precisa alternar rapidamente entre milhares de processos. O escalonador (scheduler) do kernel é responsável por decidir qual processo ganha tempo de CPU e por quanto tempo. Durante sua existência, um processo transita por diferentes estados:

    - **Running (R):** O processo está ativamente executando na CPU ou pronto para executar.
    - **Sleeping (S ou D):** O processo está ocioso, aguardando algum evento ou recurso para continuar (S = interruptível, D = ininterruptível, geralmente aguardando resposta do disco).
    - **Stopped (T):** O processo foi suspenso/pausado.
    ```bash
    # Pressionar Ctrl+Z no terminal enquanto um processo interativo roda o coloca em estado Stopped (T).
    ```
    - **Zombie (Z):** O processo já terminou sua execução e "morreu", mas ainda possui uma entrada na tabela de processos porque o processo pai ainda não leu seu status de encerramento.

    ---

    ### Process, Thread, User e Group IDs
    Para gerenciar a segurança e o controle, o sistema atribui identificadores numéricos a tudo:

    - **PID (Process ID):** Um número único atribuído a cada processo assim que ele é criado. O sistema usa o PID para rastrear o processo.
    - **TID (Thread ID):** Em processos multi-threaded, cada thread recebe um TID para identificar as diferentes linhas de execução internas.
    - **UID (User ID) e GID (Group ID):** Todo processo roda com as permissões do usuário e do grupo que o iniciou. O UID e o GID determinam a quais arquivos e recursos do sistema aquele processo terá permissão de acessar.

    ---

    ### Encerrando e Priorizando Processos
    Processos podem ser encerrados enviando "sinais" a eles (geralmente usando o comando kill seguido do PID). O sinal mais comum pede que o processo encerre graciosamente (SIGTERM - 15), enquanto outros forçam a parada imediata (SIGKILL - 9).
    ```bash
    kill 1234      # Envia sinal padrão (15) para encerrar o processo com PID 1234 graciosamente
    kill -9 1234   # Força o encerramento imediato do processo com PID 1234
    killall firefox # Encerra todos os processos com o nome "firefox"
    ```

    Sobre Prioridades (nice e renice): Nem todos os processos têm a mesma importância. O Linux usa um valor chamado nice (niceness) para definir a prioridade de um processo perante a CPU.
    O valor nice varia de -20 (maior prioridade) a 19 (menor prioridade).
    Quanto menor o número, menos "legal" (nice) o processo é com os outros, pegando mais tempo de CPU para ele.

    O comando nice inicia um programa com uma prioridade específica:
    ```bash
    nice -n 10 ./meu_script.sh  # Inicia o script com prioridade menor (valor 10)
    sudo nice -n -5 tar -czf backup.tar.gz /home # Inicia backup com prioridade alta (-5)
    ```

    O comando renice altera a prioridade de um processo que já está em execução:
    ```bash
    renice -n 5 -p 1234   # Altera a prioridade do processo PID 1234 para 5
    sudo renice -n -10 -p 1234 # Requer root para definir prioridade negativa (alta)
    ```

    ---

    ### Métricas e Controle: Load Averages
    O Load Average (média de carga) é uma métrica crucial que indica o volume de demanda sobre o sistema. Ele representa a média de processos que estão usando a CPU ou aguardando para usá-la. Ao visualizar o Load Average (usando comandos como top ou uptime), você verá três números:
    - A média do último 1 minuto.
    - A média dos últimos 5 minutos.
    - A média dos últimos 15 minutos.
    ```bash
    uptime  # Mostra quanto tempo o sistema está ligado e os 3 valores de Load Average
    ```

    Interpretação: Em um sistema com 1 núcleo de CPU, um load average de 1.00 significa que a CPU está 100% utilizada. Um valor de 0.50 significa 50% de uso. Se o valor passar de 1.00 (ex: 1.50), significa que o sistema está sobrecarregado e processos estão na fila esperando.

    ---

    ### Background e Foreground (Managing Jobs)
    No terminal, você pode gerenciar como os trabalhos (jobs) são executados:

    - **Foreground (Primeiro plano):** O comando ocupa o terminal e você não pode digitar novos comandos até que ele termine.
    - **Background (Segundo plano):** Adicionando um & ao final do comando, ele roda em background, devolvendo o terminal para você usar imediatamente. 
    ```bash
    tar -czf backup.tar.gz /home &  # Executa o backup em background
    ```

    Você pode listar e gerenciar esses trabalhos movendo-os entre os dois estados usando os comandos jobs, fg (traz para o foreground) e bg (manda para o background).
    ```bash
    jobs       # Lista todos os processos rodando ou parados no terminal atual
    fg %1      # Traz o job número 1 (listado no comando anterior) para o foreground
    bg %2      # Força o job número 2 (que estava pausado) a continuar rodando em background
    ```

    ---

    ### Listando Processos: ps
    O comando ps tira uma "fotografia" (um retrato estático) dos processos no exato momento em que é executado. Ele possui duas sintaxes históricas principais:

    - **System V Style:** Usa opções precedidas por um traço.
    ```bash
    ps -e   # Mostra todos os processos do sistema
    ps -f   # Mostra formato de listagem completa
    ps -ef  # Combina os dois para uma visão geral e detalhada
    ```

    - **BSD Style:** Usa opções sem o traço.
    ```bash
    ps aux  # 'a' (todos usuários), 'u' (orientado ao usuário), 'x' (sem terminal anexado)
    ```

    - **Process Tree (Árvore de Processos):** Mostra a hierarquia de quem iniciou quem (processo pai e processo filho), útil para entender a dependência entre eles.
    ```bash
    pstree  # Exibe a árvore visual de processos
    ```

    ---

    ### Monitoramento em Tempo Real: top
    Diferente do ps, o top é um monitor de sistema interativo e dinâmico, atualizado em tempo real. A tela do top é dividida em duas partes: o cabeçalho de status e a lista de processos.
    ```bash
    top
    ```

    Entendendo o cabeçalho do top:
    - **Primeira linha:** Mostra a hora atual, o uptime (tempo que o sistema está ligado), usuários logados e o Load Average (1, 5 e 15 min).
    - **Segunda linha:** Resumo de Tasks (Tarefas/Processos) e quantos estão em cada estado (Running, Sleeping, Stopped, Zombie).
    - **Terceira linha:** Uso de CPU. Mostra a porcentagem de tempo gasta em processos de usuário (us), processos do sistema (sy), processos com prioridade alterada (ni) e tempo ocioso (id).
    - **Quarta e Quinta linhas:** Uso de Memória Física (RAM) e Memória Virtual (Swap), mostrando o total, livre, usado e o que está em cache/buffers.

    Interactive Keys (Teclas Interativas): Com o top aberto, você pode pressionar teclas para agir sobre os processos:
    - **k** para matar (kill) um processo.
    - **r** para alterar a prioridade (renice) de um processo.
    - **q** para sair do programa.

    ---

    ### Iniciando Processos no Futuro
    Nem sempre você quer que um comando rode imediatamente. O Linux oferece ferramentas para agendamento:

    - **at:** Usado para agendar um comando ou script para rodar apenas uma única vez em um horário específico no futuro.
    ```bash
    at 15:30       # Abre um prompt para digitar os comandos que rodarão às 15:30 de hoje
    at now + 1 hour # Roda o comando daqui a 1 hora
    ```

    - **cron:** O daemon de agendamento de tarefas recorrentes. Usado para executar comandos em intervalos regulares (ex: todo dia às 2h da manhã, toda segunda-feira, a cada 15 minutos).
    ```bash
    crontab -e     # Abre o arquivo de agendamentos do usuário para edição
    crontab -l     # Lista os agendamentos atuais do usuário
    ```

    - **anacron:** Complementa o cron. É usado em máquinas que não ficam ligadas 24 horas por dia (como laptops). Se o computador estava desligado na hora de uma tarefa agendada, o anacron garante que ela rode assim que o sistema for ligado.
    - **sleep:** Usado em scripts ou linha de comando para adicionar um "atraso" ou pausa na execução por um tempo especificado (em segundos, minutos ou horas) antes de continuar a próxima ação.
    ```bash
    sleep 10s      # Pausa o terminal por 10 segundos
    sleep 5m       # Pausa por 5 minutos
    ```

    ---

    ### Sistema de Arquivos, Comparação e Arquivamento (Novo)
    Além da gestão de processos, é fundamental gerenciar a infraestrutura de arquivos do Linux:
    
    - **Estrutura de Diretórios e Montagem:** O arquivo `/etc/fstab` é onde verificamos quais sistemas de arquivos serão montados automaticamente quando o sistema entra em modo multiusuário (multi-user mode). Para saber se um sistema de arquivos atual está montado como somente leitura (read-only) ou leitura e escrita (read/write), usamos o comando **`mount`**. O diretório **`/root`** é o diretório pessoal da conta de superusuário (superuser account). Já o diretório **`/dev`** é onde você encontra os nós de dispositivos (device nodes). Para tornar os arquivos compartilhados disponíveis em uma rede, usa-se o comando **`exportfs`**.
    - **Identificação e Comparação:** Para verificar e descobrir qual é o tipo do arquivo nomeado "some_file", usamos o comando **`file some_file`**. Se precisarmos comparar recursivamente duas árvores de diretórios inteiras mencionando *apenas* quais arquivos são diferentes, novos ou deletados, a sintaxe correta é **`diff -qr`** (ex: `diff -qr /usr/src/linux-4.9 /usr/src/linux-4.10:`).
    - **Arquivamento e Compressão:** O comando **`tar zcvf backup.tar.gz ~`** arquivará toda a árvore de diretórios do usuário (entire home directory tree) neste único pacote. Para comprimir todos os arquivos num diretório `some_dir` junto com todos os arquivos de seus subdiretórios, usamos a recursão: **`gzip -r some_dir`**. Vale ressaltar que os comandos **`gunzip foo`** e **`gzip -d foo`** fazem exatamente a mesma coisa (True). 
    - **Sincronização de Rede:** O **`rsync`** é uma ferramenta de cópia de rede inteligente. Ao copiar um diretório sobre a rede para outro sistema, ele copia apenas as partes de todos os arquivos e subdiretórios que foram alteradas (only the parts that have changed), poupando banda.

    ---

    ## Conteúdo

    Neste capítulo aprendi sobre a gestão fundamental de processos, que são os programas em execução responsáveis por realizar todas as tarefas no sistema Linux. Entendi que eles podem ser interativos ou não-interativos, e que o kernel é o responsável por escaloná-los entre estados como Running, Sleeping, Stopped e Zombie.

    Aprendi que para o sistema manter a ordem, todo processo recebe um identificador único, o PID (Process ID). Para processos complexos, há também os Thread IDs (TIDs), e todos eles herdam as permissões do usuário e grupo que os iniciaram (UID e GID). Aprofundei-me na gestão de prioridade da CPU utilizando o conceito de niceness, onde aprendi que valores menores (até -20) dão maior prioridade ao processo, algo gerenciado pelo comando renice.

    A gestão de múltiplas tarefas ficou mais clara ao entender como o sistema separa processos em Foreground (prendendo o terminal) e Background (liberando o terminal). Utilizei comandos como jobs, fg e bg para gerenciar essas tarefas. O monitoramento do sistema foi um ponto alto: aprendi a interpretar o Load Average para identificar gargalos no sistema em janelas de 1, 5 e 15 minutos.

    Para visualizar tudo isso, explorei duas ferramentas essenciais. O comando ps, com seus estilos System V e BSD, para tirar "fotos" instantâneas da árvore de processos, e o comando top para um painel dinâmico em tempo real. Pude destrinchar cada uma das 5 linhas de cabeçalho do top, entendendo exatamente como ler o consumo de CPU, Memória RAM e Swap, além de usar suas teclas interativas para matar ou alterar prioridades de processos on the fly. Aprendi a automatizar a execução de rotinas no futuro com o `at` (para tarefas únicas), `cron` (recorrentes), `anacron` (máquinas que desligam) e o comando `sleep`.

    Por fim, adicionei ao meu conhecimento as propriedades cruciais da infraestrutura de arquivos. Entendi que o `/root` abriga a home do superusuário, o `/dev` guarda os nós de dispositivos, e o `/etc/fstab` diz o que será montado automaticamente em modo multiusuário, enquanto o `mount` diz se é read/write ou read-only. Dominei o `exportfs` para rede, o `file some_file` para identificar tipos, e o `diff -qr` para comparar árvores de pastas inteiras focando apenas no que mudou. Em backups, vi que o `tar zcvf backup.tar.gz ~` salva a home tree inteira, o `gzip -r` comprime recursivamente, e que `gunzip foo` e `gzip -d foo` são comandos idênticos na prática. Coroando o aprendizado, vi que o `rsync` otimiza a cópia de rede mandando apenas os blocos que foram alterados.

    ---

    # Comandos do Capítulo

    | Comando | Descrição |
    |---------|-----------|
    | `ps` | Exibe uma listagem estática dos processos que estão rodando no sistema. |
    | `top` | Exibe um painel de monitoramento dinâmico e em tempo real dos processos e recursos. |
    | `nice` | Inicia um novo programa ou comando definindo uma prioridade (niceness) específica. |
    | `renice` | Altera a prioridade de um processo que já está em execução (usando o PID). |
    | `kill` | Envia sinais para processos, frequentemente usado para encerrá-los de forma amigável ou forçada. |
    | `jobs` | Lista todos os trabalhos (processos) iniciados no terminal atual que estão parados ou em background. |
    | `fg` e `bg` | Movem jobs (tarefas do terminal) entre o primeiro plano e segundo plano. |
    | `at` | Agenda um comando ou script para ser executado uma única vez em uma data/hora no futuro. |
    | `cron` | Serviço de agendamento para tarefas repetitivas e baseadas em intervalos regulares. |
    | `anacron` | Executa tarefas periódicas agendadas em máquinas que são desligadas frequentemente. |
    | `sleep` | Pausa a execução de comandos ou scripts no terminal por um tempo pré-determinado. |
    | `mount` | Inquire se o sistema de arquivos está montado como leitura/escrita ou somente leitura. |
    | `exportfs`| Garante que os arquivos compartilhados estejam disponíveis através de uma rede. |
    | `diff` | O `diff -qr` compara árvores de diretórios listando apenas o que é diferente. |
    | `file` | Exibe o tipo de um arquivo (ex: `file some_file`). |
    | `tar` | Ferramenta de arquivamento (ex: compactar toda a home tree do usuário). |
    | `gzip` | Ferramenta de compressão. A flag `-r` faz isso de forma recursiva. O comando `gunzip` tem a mesma função de `gzip -d`. |
    | `rsync` | Copia sobre rede transferindo apenas as partes modificadas dos arquivos/diretórios. |

    ---

    # Explicação detalhada dos Comandos Básicos do Linux

    ## ps
    O ps (Process Status) é usado para fornecer informações detalhadas de um instante específico.
    - **ps -ef (System V):** O -e seleciona todos os processos e o -f faz a listagem completa (full format), mostrando o PID, PID do pai (PPID) e comando completo.
    - **ps aux (BSD):** Muito popular. Mostra todos os processos de todos os usuários (a), adiciona colunas focadas no uso de CPU/Memória do usuário (u) e inclui processos sem terminal anexado (x).

    ## top
    O top é a ferramenta padrão de monitoramento de performance. Ele não apenas exibe processos consumindo mais CPU por padrão, mas também fornece um raio-x geral da saúde da máquina nas 5 linhas superiores. Dentro do programa, atalhos como k e r permitem intervenções diretas na tabela de processos.

    ## renice
    O renice altera o valor de agendamento (nice value) de processos ativos. Valores vão de -20 (maior prioridade, a CPU dá atenção máxima) a 19 (menor prioridade). Apenas o usuário root pode definir valores negativos. Exemplo de uso: `renice -n 5 -p 1234`.

    ## Gerenciamento de Jobs (jobs, fg, bg)
    O shell permite gerenciar múltiplos programas iniciados a partir da mesma janela de terminal usando o conceito de "jobs".
    - **& (E comercial):** Colocado no final de um comando, inicia o programa diretamente em background.
    - **Ctrl+Z:** Se um programa já estiver rodando em foreground, essa combinação o pausa (estado Stopped) e o envia para background.
    - **jobs:** Lista todos os programas pausados ou rodando em background na sessão atual.
    - **bg %numero:** Pega um job que está pausado e faz com que ele volte a executar em background.
    - **fg %numero:** Traz um job do background de volta para o foreground.

    ## Agendamento (at, cron, anacron, sleep)
    - **at:** Processa agendamentos únicos (batch processing) na hora programada.
    - **cron:** É um daemon contínuo que lê as crontabs contendo regras de tempo precisas para manutenção recorrente.
    - **anacron:** Garante que tarefas atrasadas (porque o PC estava desligado na hora marcada do cron) sejam executadas assim que o sistema ligar.
    - **sleep:** Suspende a chamada do terminal ou a execução de um script shell. Aceita sufixos como s (segundos), m (minutos), h (horas).

    ## Sistema de Arquivos, Localizações e Compartilhamento
    - **`/etc/fstab`:** Configuração lida durante a inicialização que determina quais sistemas de arquivos serão automaticamente montados no multi-user mode.
    - **`mount`:** Quando executado, permite indagar e verificar se um filesystem está como read-only (apenas leitura) ou read/write (leitura e escrita).
    - **`/root` e `/dev`:** O `/root` é especificamente o diretório home da conta superuser. O `/dev` é o repositório de device nodes.
    - **`exportfs`:** Comando vital para servidores de arquivos; assegura que as pastas marcadas como "shared" sejam publicadas e disponibilizadas over a network (através da rede).

    ## Arquivamento, Compressão e Comparação
    - **`file`:** Ao digitar `file some_file`, o sistema não olha para a extensão do nome do arquivo, mas inspeciona o cabeçalho binário interno para te dizer qual o tipo real do arquivo.
    - **`diff -qr`:** Comparação de árvores (`-r` para recursivo). A opção `-q` (brief) faz com que ele não mostre linha a linha o que mudou no texto, mas apenas mencione *quais arquivos* são novos, deletados ou estão diferentes.
    - **`tar`:** Ao executar `tar zcvf backup.tar.gz ~`, ele zípa (z), cria (c), exibe o progresso (v) num arquivo (f) chamado backup.tar.gz englobando toda a árvore completa do diretório home do usuário logado (simbolizado pelo til `~`).
    - **`gzip` e `gunzip`:** O `gzip -r some_dir` comprime todos os arquivos soltos dentro da pasta indicada e desce nas subpastas comprimindo os de lá também. Para reverter, você pode digitar `gunzip foo` ou `gzip -d foo`, os dois fazem a exata mesma ação.
    - **`rsync`:** A magia do rsync em transferências de rede é não copiar o que já existe no destino. Ele escaneia blocos e transfere *apenas as partes* dos arquivos e diretórios que sofreram alterações.

    ## Recursos úteis
    https://linuxcommand.org  
    https://kernel.org  
    https://gnu.org