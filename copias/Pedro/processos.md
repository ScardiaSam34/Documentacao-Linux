# Processos do Linux
Um **processo** é essencialmente uma instância de um programa em execução. Quando você executa um comando ou abre um aplicativo, o kernel do Linux carrega o código binário na memória RAM e aloca recursos para ele.

### Tipos de Processos
* **Processos de Primeiro Plano (Foreground):** Iniciados pelo usuário e conectados ao terminal. O shell aguarda a sua conclusão para permitir novos comandos.
* **Processos de Segundo Plano (Background):** Executam sem ocupar a interface do terminal, permitindo que o usuário continue trabalhando.
* **Daemons:** Processos de sistema que rodam permanentemente em segundo plano, geralmente iniciando no boot (ex: `sshd`, `systemd`).
* **Processos Zumbis:** Processos que terminaram sua execução, mas ainda possuem uma entrada na tabela de processos porque o processo pai ainda não leu seu status de saída.

---

## 1. Atributos de um Processo

Cada processo possui metadados que o identificam e definem suas permissões:

* **PID (Process ID):** Identificador numérico único.
* **PPID (Parent Process ID):** O PID do processo que gerou este processo.
* **UID / User:** O usuário dono do processo.
* **Prioridade (PR) e Nice (NI):** Determinam a prioridade de CPU. O valor *Nice* varia de -20 (maior prioridade) a 19 (menor prioridade).

---

## 2. Monitoramento com `ps` e `top`

### Comando `ps` (Snapshot estático)
Exibe o estado dos processos no exato momento da execução.
* `ps aux`: Mostra todos os processos de todos os usuários com detalhes de CPU e memória.
* `ps -ef`: Formato padrão para visualizar a hierarquia e o PPID.

### Comando `top` (Monitoramento em tempo real)
Fornece uma visão dinâmica e interativa do sistema.
* **Atalhos dentro do top:**
    * `M`: Ordena por uso de Memória.
    * `P`: Ordena por uso de CPU.
    * `k`: Mata um processo (solicita o PID).
    * `q`: Sai do programa.

---

## 3. Métricas e Mediadores de Carga

### Load Average (Média de Carga)
Exibido no comando `top` ou `uptime`, o *Load Average* mostra a carga do sistema em 1, 5 e 15 minutos.
* Se o valor for igual ao número de núcleos da CPU, o sistema está em uso pleno.
* Valores acima do número de núcleos indicam que processos estão na fila aguardando processamento.

### Outras Métricas
* **RSS (Resident Set Size):** Memória RAM física real utilizada.
* **%CPU:** Percentual de tempo de CPU que o processo está consumindo.

---

## 4. Manipulação: Foreground vs Background

Você pode gerenciar como os processos ocupam o seu terminal:

* **Enviar para o Background na execução:** Adicione um `&` ao final do comando.
    * Ex: `cp arquivo_gigante.iso /backup/ &`
* **Pausar e enviar para Background:**
    1. Pressione `Ctrl + Z` (suspende o processo atual).
    2. Digite `bg` para que ele continue rodando em segundo plano.
* **Trazer para o Primeiro Plano:** Digite `fg %<id_do_job>`.
* **Listar jobs ativos:** Use o comando `jobs`.

---

## 5. Agendamento e Pausas

### `sleep`: Pausar a execução
Suspende a execução por um tempo determinado.
* `sleep 10 && echo "Acordei"` (espera 10 segundos antes de imprimir).

### `at`: Execução única no futuro
Ideal para tarefas que devem rodar uma única vez.
* Ex: `echo "reboot" | at 02:00` (agenda um reboot para as 2 da manhã).

### `cron`: Agendamento recorrente
O `crontab` é usado para tarefas periódicas (backups diários, limpezas semanais).
* `crontab -e`: Edita o arquivo de tarefas.
* **Sintaxe:** `minuto hora dia mes dia_da_semana comando`
    * `0 5 * * * /path/script.sh` (executa todo dia às 05:00).