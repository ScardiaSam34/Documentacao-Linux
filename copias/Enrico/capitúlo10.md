## 10. Processos e Sinais
### Um processo é um programa em execução.

Gerenciamento de Processos no Linux
* 1. Identificação e Natureza
Um processo é uma instância de um programa em execução. Para que o Kernel o gerencie, ele utiliza:

PID (Process ID): Um número único de identificação. O PID 1 (geralmente o systemd) é o ancestral de todos os outros processos.

Threads: Um processo pode ser single-thread (uma linha de execução) ou multi-thread (várias tarefas paralelas dentro do mesmo processo, como um navegador abrindo várias abas).

Tipos: * Interativos: Exigem entrada do usuário (ex: editores de texto).

Não interativos (Daemons): Rodam em segundo plano (ex: servidores de banco de dados).

* 2. Priorização: O Valor "Nice"
O sistema utiliza o conceito de Niceness (bondade) para decidir quem recebe mais tempo de CPU.

A escala vai de -20 (maior prioridade/menos bondoso) a 19 (menor prioridade/mais bondoso).

Um processo com valor 19 "deixa" os outros passarem na frente, enquanto o -20 "atropela" os demais.

* 3. Monitoramento e Performance
Para entender a saúde do sistema, usamos:

ps: Fornece um "retrato" estático dos processos no momento da execução.

top: Uma interface dinâmica que atualiza em tempo real o uso de CPU e memória.

Load Average (Média de Carga): Indica a carga do sistema nos últimos 1, 5 e 15 minutos. Se os valores forem superiores ao número de núcleos da CPU, o sistema está sobrecarregado.

* 4. Controle de Execução (Foreground vs Background)
O Shell permite alternar como você interage com as tarefas.

Foreground (Primeiro Plano): O processo ocupa o terminal e você deve esperar ele terminar para digitar outro comando.

Background (Segundo Plano): Você adiciona um & ao final do comando para que ele execute "atrás", liberando o terminal imediatamente.

Exemplo: cp arquivo_gigante.iso /backup/ &

Controle: Use jobs para listar, fg para trazer para frente e bg para enviar para trás.

* 5. Automação e Agendamento
O Linux permite que você "configure e esqueça" tarefas repetitivas ou futuras.

Comando at: Usado para execuções únicas no futuro. Ex: "Execute este script às 15:00 de hoje".

Serviço cron: O padrão para tarefas recorrentes. Configurado via crontab -e, permite definir execuções em minutos, horas, dias do mês, meses ou dias da semana (ex: backup toda segunda-feira às 03:00 da manhã).

Sinais (Signals): SIGTERM (15) pede para o programa fechar; SIGKILL (9) força o encerramento imediato.

Load Average: Aqueles três números no top que indicam a carga da CPU nos últimos 1, 5 e 15 minutos.