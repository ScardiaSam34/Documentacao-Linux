# 🔹 Capítulo 12 – User Environment

## 🔹 Tópicos
- Contas, Usuários e Grupos
- Variáveis de Ambiente (Environment Variables)
- Relembrando Comandos Anteriores (Histórico)
- Permissões de Arquivos e Propriedade

---

## 🔹 Subtópicos

### Contas, Usuários e Grupos
O Linux é um sistema operacional multiusuário, o que significa que várias pessoas podem estar logadas e executando tarefas simultaneamente sem interferir umas nas outras. 
- **Identificando o Usuário:** Para saber quem está logado no sistema, utiliza-se o comando `who`. Para descobrir com qual identificação (User ID) você está operando no momento em um terminal específico, usa-se o comando `whoami`.
- **Adicionando e Removendo:** Administradores podem criar novas contas de usuário e grupos para organizar permissões e acessos dentro do sistema.

### A Conta root e Elevação de Privilégios (su e sudo)
A conta **root** (superusuário) tem acesso total e irrestrito a todo o sistema. É considerado perigoso e uma má prática usar o root para tarefas diárias, pois um comando errado pode destruir o sistema.
Para tarefas administrativas, usuários comuns podem elevar seus privilégios temporariamente:
- **`su` (Substitute User):** Permite trocar para a conta root (ou outro usuário) exigindo a senha do usuário alvo. O terminal passa a operar integralmente como aquele usuário.
- **`sudo` (Superuser DO):** Permite que um usuário comum execute um comando específico com privilégios de root, usando a sua própria senha. É a forma mais segura e recomendada de realizar tarefas administrativas.

### Arquivos de Inicialização (Startup Files) e Aliases
Quando um usuário faz login, o shell (geralmente o `bash`) lê vários arquivos de configuração (Startup Files) em uma ordem específica para construir o ambiente de trabalho daquele usuário.
- **Ordem e Escopo:** O arquivo `/etc/profile` é lido primeiro e aplica configurações globais para todos os usuários. Em seguida, o shell lê arquivos ocultos no diretório pessoal do usuário (como `~/.bash_profile` e `~/.bashrc`), que personalizam apenas o ambiente dele.
- **Vantagens:** Esses arquivos configuram o tipo de terminal, editor de texto padrão e o prompt da linha de comando.
- **Aliases (Apelidos):** Você pode criar atalhos personalizados para comandos longos usando `alias` (ex: `alias atualizar='sudo apt update'`). Para que o alias seja permanente e esteja disponível sempre que abrir o terminal, ele deve ser salvo no arquivo `~/.bashrc`.

### Variáveis de Ambiente (Environment Variables)
Uma variável de ambiente é uma string (texto) que contém dados usados pelo shell e por aplicativos para entender como se comportar. Elas podem ser personalizadas para adequar o sistema às suas necessidades. Exemplos principais:
- **`HOME`:** Armazena o caminho absoluto do diretório pessoal do usuário atual (ex: `/home/joao`).
- **`PATH`:** Uma lista de diretórios separados por dois-pontos (`:`). Quando você digita um comando, o Linux procura o arquivo executável apenas nos diretórios listados no `PATH`. (Ex: Para rodar scripts de uma pasta `/tmp`, ela precisaria ser adicionada ao `PATH`).
- **`SHELL`:** Indica qual é o interpretador de comandos padrão do usuário (geralmente `/bin/bash`).
- **`PS1`:** Define a aparência do seu prompt de comando (o texto que aparece antes de você digitar, geralmente mostrando `usuario@maquina:~$`).

### Relembrando Comandos (History e Atalhos)
O shell mantém um registro de tudo o que você digita, economizando muito tempo de digitação e evitando erros.
- **Comando `history`:** Mostra uma lista numerada dos comandos executados anteriormente.
- **Variáveis de Histórico:** O tamanho desse histórico é controlado por variáveis de ambiente como `HISTSIZE` (comandos lembrados na memória atual) e `HISTFILESIZE` (comandos salvos no arquivo físico `.bash_history`).
- **Atalhos de Teclado (Keyboard Shortcuts):** O Linux suporta atalhos essenciais na linha de comando, como usar as setas do teclado (Cima/Baixo) para navegar pelo histórico, ou `Ctrl+R` para fazer uma busca reversa e encontrar um comando longo digitado no passado.

### Permissões de Arquivos e Propriedade
A segurança do Linux é baseada na propriedade e nas permissões de cada arquivo e diretório.
- **Propriedade (Ownership):** Todo arquivo pertence a um Usuário Dono (Owner) e a um Grupo Dono (Group).
- O comando **`chown`** altera o usuário dono do arquivo.
- O comando **`chgrp`** altera o grupo dono do arquivo.
- **Modos de Permissão (chmod):** As permissões definem quem pode Ler (Read), Gravar/Modificar (Write) e Executar (Execute) o arquivo. O comando **`chmod`** é usado para alterar essas regras, garantindo que usuários não autorizados não acessem ou modifiquem dados sensíveis.

---

# 🔹 Conteúdo

Neste capítulo, compreendi como o Linux gerencia o ambiente de múltiplos usuários. Aprendi que, por ser um sistema multiusuário, é vital saber identificar quem está logado utilizando comandos como `who` e `whoami`. Entendi o papel crítico da conta `root`, que possui poder absoluto sobre o sistema, e por que é uma prática ruim usá-la o tempo todo. Em vez disso, descobri que devo usar o comando `sudo` para executar tarefas administrativas de forma temporária e segura, usando minha própria senha.

Aprofundei-me na construção do ambiente de trabalho do usuário, que é montado através de "Startup Files" (arquivos de inicialização). Entendi que o `/etc/profile` afeta todos os usuários, enquanto arquivos como o `~/.bashrc` são pessoais. É nesses arquivos que posso salvar personalizações permanentes, como a criação de `aliases` (atalhos para comandos longos) e a modificação de Variáveis de Ambiente. Descobri que variáveis como `HOME`, `SHELL` e `PS1` ditam o comportamento e a aparência do meu terminal, e que a variável `PATH` é fundamental, pois diz ao sistema exatamente em quais diretórios procurar quando eu digito um comando.

Para aumentar minha produtividade na linha de comando, aprendi a utilizar o comando `history`, que armazena os comandos passados. Vi que posso resgatar comandos antigos usando as setas do teclado ou atalhos de busca, evitando ter que redigitar instruções complexas. 

Por fim, consolidei meus conhecimentos sobre a segurança no sistema de arquivos. Entendi que todo arquivo tem um usuário e um grupo dono, que podem ser alterados com os comandos `chown` e `chgrp`, respectivamente. Para controlar o acesso a esses arquivos, aprendi a usar o comando `chmod`, que me permite definir com precisão quem pode ler, editar ou executar um determinado arquivo ou diretório no sistema.

---

# Comandos do Capítulo

| Comando | Descrição |
|--------|-----------|
| `who` | Exibe uma lista de todos os usuários que estão atualmente logados no sistema. |
| `whoami` | Mostra o nome do usuário efetivo (User ID) que está executando o terminal no momento. |
| `su` | Substitui o usuário atual por outro (geralmente o root), exigindo a senha do usuário de destino. |
| `sudo` | Executa um comando com privilégios de superusuário (root), exigindo a senha do próprio usuário. |
| `alias` | Cria atalhos personalizados e curtos para comandos longos ou complexos. |
| `history` | Exibe a lista numerada de comandos executados anteriormente no terminal. |
| `chmod` | Altera as permissões de acesso (Leitura, Escrita, Execução) de um arquivo ou diretório. |
| `chown` | Altera o usuário proprietário (dono) de um arquivo ou diretório. |
| `chgrp` | Altera o grupo proprietário de um arquivo ou diretório. |

# Explicação detalhada dos Comandos Básicos do Linux

## who e whoami
- **`who`:** Útil em servidores para ver quem mais está acessando a máquina simultaneamente. Mostra o nome do usuário, o terminal que estão usando e a data/hora do login.
- **`whoami`:** Muito usado em scripts ou após usar comandos de elevação de privilégio para ter certeza de qual conta você está controlando naquele exato momento (ex: verificar se você ainda é "root" ou voltou a ser seu usuário normal).

## su e sudo
- **`su` (Substitute User):** Ao digitar apenas `su -`, o sistema pedirá a senha do administrador (root) e mudará todo o seu terminal para o ambiente do root. Para sair, deve-se digitar `exit`.
- **`sudo` (Superuser DO):** Prefixo usado antes de qualquer comando (ex: `sudo apt update`). O sistema verifica se seu usuário tem permissão no arquivo de configuração (sudoers), pede a sua senha pessoal, executa aquele comando específico como root e imediatamente devolve o terminal ao seu usuário comum.

## alias
Cria macros/atalhos para facilitar o trabalho.
- Se você digita `ls -la --color=auto` com frequência, pode criar um atalho digitando: `alias ll='ls -la --color=auto'`. A partir desse momento, digitar apenas `ll` executará o comando completo. Para remover, usa-se `unalias ll`.

## history
Exibe o histórico de comandos. 
- Você pode reexecutar um comando específico do histórico usando o ponto de exclamação seguido do número do comando. Exemplo: se o comando `sudo systemctl restart apache2` é o número 105 no histórico, digitar `!105` e pressionar Enter o executará novamente.

## chmod (Change Mode)
Altera as permissões de arquivos. Pode ser usado com letras (r=read, w=write, x=execute) ou números octais.
- Exemplo por letras: `chmod +x script.sh` (Adiciona permissão de execução ao arquivo, tornando-o um programa que pode ser rodado).
- As permissões determinam o que o dono, o grupo e os outros usuários (resto do mundo) podem fazer com aquele dado.

## chown e chgrp
- **`chown` (Change Owner):** Transfere a propriedade absoluta do arquivo. Apenas o root pode mudar o dono de um arquivo livremente. Exemplo: `sudo chown maria relatorio.txt` (faz a usuária "maria" ser a nova dona do arquivo).
- **`chgrp` (Change Group):** Muda a qual grupo o arquivo pertence. Exemplo: `chgrp financeiro planilha.csv` (permite que usuários do grupo "financeiro" apliquem suas permissões ao arquivo). O `chown` também pode fazer as duas coisas ao mesmo tempo usando a sintaxe `chown dono:grupo arquivo`.

---

## 🔹 Recursos úteis
https://linuxcommand.org 
https://kernel.org 
https://gnu.org