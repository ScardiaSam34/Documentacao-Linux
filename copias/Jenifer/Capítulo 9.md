# Capítulo 9 — Processos no Linux

No Linux, tudo que está sendo executado no sistema é chamado de **processo**. Quando você abre um programa, executa um comando ou até mesmo quando o sistema realiza tarefas internas, tudo isso acontece por meio de processos. Eles são fundamentais para o funcionamento do sistema, pois representam as atividades em execução.

Um processo pode ser simples, executando apenas uma tarefa **(thread única)**, ou mais complexo, utilizando múltiplas threads para realizar várias operações ao mesmo tempo. Por exemplo, um navegador pode carregar páginas, executar scripts e reproduzir vídeos simultaneamente, tudo dentro do mesmo processo, usando múltiplas threads.

Cada processo possui um identificador único chamado **PID (Process ID)**. Esse número é utilizado pelo sistema para controlar e gerenciar os processos. Além disso, existe também o **PPID (Parent Process ID)**, que indica qual processo criou aquele processo. Isso cria uma espécie de hierarquia de processos dentro do sistema.

Os processos podem ser classificados de diferentes formas. Existem processos **interativos**, que dependem da ação do usuário (como um comando digitado no terminal), e processos **não interativos**, que rodam automaticamente em segundo plano, como serviços do sistema (daemons).

---

## Monitoramento de processos

Para visualizar os processos em execução, o Linux oferece vários comandos. Um dos mais básicos é:

```bash
ps
```

Ele mostra uma lista dos processos ativos naquele momento. Para ver mais detalhes, pode-se usar:

```bash
ps aux
```

Esse comando exibe informações como usuário, PID, uso de CPU, memória e o comando que iniciou o processo.

Outro comando muito importante é:

```bash
top
```

O `top` mostra os processos em tempo real, atualizando constantemente. Ele permite ver quais processos estão consumindo mais CPU ou memória, sendo muito útil para monitoramento do sistema.

---

## Prioridade de processos (nice)

Nem todos os processos têm a mesma prioridade. O Linux permite controlar isso usando o valor chamado `nice`.

Esse valor varia de **-20 a 19**:

- Valores menores (ex: -20) → maior prioridade
- Valores maiores (ex: 19) → menor prioridade

Exemplo de execução com prioridade diferente:

```bash
nice -n 10 comando
```

Isso faz o processo rodar com prioridade menor, sem prejudicar outros processos mais importantes.

---

## Execução em foreground e background

No Linux, um processo pode rodar em:

- **Foreground (primeiro plano):** ocupa o terminal
- **Background (segundo plano):** roda “por trás”, liberando o terminal

Para rodar um comando em background:

```bash
comando &
```

Exemplo:

```bash
sleep 30 &
```

Você também pode pausar um processo com `Ctrl + Z` e depois colocá-lo em background com:

```bash
bg
```

Para trazer de volta ao primeiro plano:

```bash
fg
```

---

## Média de carga (load average)

O sistema Linux mede o uso da CPU através da chamada **média de carga (load average)**. Esse valor indica quantos processos estão sendo executados ou aguardando execução.

Normalmente aparecem três números, por exemplo:

```bash
1.00 0.75 0.50
```

Eles representam a média de carga nos últimos:

- 1 minuto
- 5 minutos
- 15 minutos

Se o valor estiver muito alto, pode indicar que o sistema está sobrecarregado.

---

## Agendamento de tarefas

O Linux permite automatizar tarefas usando agendadores.

O comando `at` é usado para executar uma tarefa **uma única vez**, em um horário específico:

```bash
at 15:00
```

Depois você digita o comando que deseja executar.

Já o `cron` é usado para tarefas **repetitivas**, como executar algo todos os dias ou toda semana.

Para editar tarefas do cron:

```bash
crontab -e
```

Exemplo de agendamento:

```bash
0 8 * * * echo "Bom dia"
```

Isso executa o comando todos os dias às 8h.
