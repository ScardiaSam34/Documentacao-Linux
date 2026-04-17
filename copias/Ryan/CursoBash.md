# 🔹 Capítulo 1 – Introdução ao Terminal e Navegação

## 🔹 Tópicos
- Introdução
- O que é o Terminal e o Bash?
- A Árvore de Diretórios do Linux
- Descobrindo onde você está (pwd)
- Listando arquivos e pastas (ls)
- Navegando entre diretórios (cd)

## 🔹 Subtópicos

### Introdução
Este capítulo marca o primeiro contato com a tela preta do Linux. Para quem está acostumado a usar o mouse e clicar em pastas, o terminal pode parecer assustador, mas ele é apenas uma forma de conversar com o computador usando texto. Aqui, você aprenderá a se localizar dentro do sistema e a caminhar pelas pastas sem precisar de uma interface gráfica.

### O que é o Terminal e o Bash?
O **Terminal** é a janela preta onde você digita comandos. O **Bash** (Bourne Again Shell) é o programa de fato que roda dentro do terminal. Ele lê o que você digita, traduz para o sistema operacional e devolve a resposta na tela. Pense no terminal como o telefone e no Bash como o idioma que você usa para falar com o sistema.

### A Árvore de Diretórios do Linux
No Windows, as coisas ficam dentro do "Disco C:". No Linux, tudo começa na "Raiz", representada por uma barra diagonal: **/**. A partir da raiz, o sistema se ramifica como uma árvore invertida. Pastas importantes incluem a **/home** (onde ficam os arquivos pessoais dos usuários) e a **/etc** (onde ficam as configurações dos programas).

### Descobrindo onde você está (pwd)
Ao abrir o terminal, você está em algum lugar dentro do computador. Para descobrir exatamente em qual pasta você se encontra, utilizamos o comando que imprime o diretório de trabalho atual.

```bash
pwd
```

### Listando arquivos e pastas (ls)
Saber onde você está é importante, mas saber o que tem lá dentro é ainda mais. O comando "ls" (abreviação de list) mostra todos os arquivos e pastas visíveis no local atual. Ele possui opções (chamadas de flags) que revelam arquivos ocultos ou mostram detalhes como tamanho e data de criação.

```bash
ls -la
```

### Navegando entre diretórios (cd)
Para mudar de pasta, usamos o comando "cd" (change directory). Você pode informar o caminho completo de onde quer ir (caminho absoluto) ou apenas dar um passo em relação a onde você já está (caminho relativo). Para voltar uma pasta para trás, usamos dois pontos "..".

```bash
cd /home/usuario/Documentos
```

# 🔹 Conteúdo

Neste capítulo, aprendi a base da sobrevivência no terminal Linux. Compreendi que o Bash é o tradutor dos meus comandos em texto e que o sistema de arquivos do Linux não usa letras de unidades como o Windows, mas sim uma grande árvore que começa na raiz (/). Aprendi a me localizar usando o comando pwd para não me perder, listei os arquivos do meu diretório atual e descobri como ver até os arquivos ocultos com as flags do comando ls. Por fim, consegui caminhar livremente pelo sistema usando o cd, aprendendo a avançar para novas pastas e a voltar quando necessário.

# Comandos do Capítulo

| Comando | Descrição |
|---------------|-----------|
| pwd | Mostra o caminho completo da pasta atual (Print Working Directory). |
| ls | Lista os arquivos e pastas do diretório atual. |
| ls -l | Lista os itens exibindo detalhes (permissões, tamanho, dono, data). |
| ls -a | Lista todos os itens, incluindo os arquivos ocultos (que começam com um ponto). |
| cd [pasta] | Entra no diretório especificado (Change Directory). |
| cd .. | Volta um nível de pasta (sobe para a pasta pai). |
| cd ~ | Leva você diretamente para o seu diretório pessoal (/home/seu_usuario). |

# Explicação detalhada dos Comandos Básicos do Linux

## Caminho Absoluto vs Caminho Relativo
Um conceito que causa muita confusão no início é como dizer ao Linux onde ir. 
O **caminho absoluto** é como dar o endereço completo de uma casa, incluindo cidade e estado. Ele sempre começa na raiz (/). Exemplo: /home/usuario/fotos. Não importa onde você esteja no sistema, esse caminho sempre te levará para o mesmo lugar.
O **caminho relativo** é como dar uma direção do tipo "vire na próxima esquina". Ele não começa com a barra (/) e depende de onde você está agora. Se você já está na pasta "usuario", você apenas diz para entrar em "fotos".

## 🔹 Recursos úteis
- [Linux Command](http://linuxcommand.org)
- [The Linux Kernel Archives](https://kernel.org)
- [The GNU Operating System](https://gnu.org)

---

# 🔹 Capítulo 2 – Manipulação de Arquivos e Diretórios

## 🔹 Tópicos
- Introdução
- Criando e apagando diretórios (mkdir e rmdir)
- Criando arquivos vazios (touch)
- Lendo arquivos de texto (cat e less)
- Copiando itens (cp)
- Movendo e renomeando itens (mv)
- Apagando arquivos e pastas com segurança (rm)

## 🔹 Subtópicos

### Introdução
Agora que você sabe navegar, é hora de começar a interagir com o sistema. Neste capítulo, você aprenderá a criar, copiar, mover, ler e excluir arquivos e pastas. Dominar esses comandos substituirá completamente a necessidade de usar o mouse para organizar seus documentos.

### Criando e apagando diretórios (mkdir e rmdir)
Para criar uma nova pasta, usamos o comando "mkdir" (make directory). Para remover uma pasta, podemos usar o "rmdir" (remove directory), porém ele só funciona se a pasta estiver completamente vazia.

```bash
mkdir MeusProjetos
```

### Criando arquivos vazios (touch)
O comando "touch" serve para criar um arquivo de texto vazio instantaneamente. É muito útil quando você precisa de um arquivo em branco para preencher depois ou para testar permissões.

```bash
touch notas.txt
```

### Lendo arquivos de texto (cat e less)
Se você quer ver o que está escrito dentro de um arquivo sem abri-lo em um editor completo, use o "cat" (concatenate). Ele joga todo o texto na sua tela de uma vez. Se o texto for muito longo, o "less" é a melhor opção, pois permite rolar o texto linha por linha.

```bash
cat notas.txt
```

### Copiando itens (cp)
O "cp" (copy) duplica arquivos ou pastas. Você informa primeiro o que quer copiar, e depois para onde quer enviar a cópia. Se for copiar uma pasta inteira e seu conteúdo, é preciso adicionar a flag -r (recursivo).

```bash
cp arquivo.txt /home/usuario/Documentos/
```

### Movendo e renomeando itens (mv)
O "mv" (move) recorta um arquivo de um lugar e cola no outro. Curiosamente, no Linux não existe um comando específico apenas para "renomear". Renomear é, na prática, "mover" o arquivo para a mesma pasta, mas com um nome diferente.

```bash
mv velho.txt novo.txt
```

### Apagando arquivos e pastas com segurança (rm)
O "rm" (remove) apaga arquivos permanentemente. Diferente do Windows, o terminal do Linux **não tem lixeira**. Se você apagar, sumiu. Para apagar uma pasta cheia de arquivos, usamos o perigoso "rm -r".

```bash
rm arquivo.txt
```

# 🔹 Conteúdo

Neste capítulo, aprendi como moldar o ambiente de arquivos ao meu favor. Descobri como criar pastas com o mkdir e arquivos em branco rápidos com o touch. Entendi como visualizar o conteúdo de documentos diretamente na tela do terminal usando o cat e o less. Mais importante, dominei a arte de organizar meus dados, utilizando o cp para duplicar, o mv para mover e renomear itens, e tomei muito cuidado ao aprender sobre o rm, entendendo que não existe lixeira no terminal do Linux e que o modo recursivo (-r) deve ser usado com extrema cautela.

# Comandos do Capítulo

| Comando | Descrição |
|---------------|-----------|
| mkdir [nome] | Cria um novo diretório (pasta). |
| rmdir [nome] | Remove um diretório, mas apenas se estiver vazio. |
| touch [nome] | Cria um arquivo vazio ou atualiza a data de modificação de um existente. |
| cat [arquivo] | Exibe todo o conteúdo do arquivo na tela do terminal. |
| less [arquivo]| Abre o arquivo de forma interativa, permitindo rolar com as setas do teclado (aperte "q" para sair). |
| cp [orig] [dest]| Copia um arquivo da origem para o destino. |
| cp -r [orig] [dest]| Copia uma pasta inteira e tudo o que há dentro dela (Recursivo). |
| mv [orig] [dest]| Move ou renomeia um arquivo ou pasta. |
| rm [arquivo] | Exclui um arquivo permanentemente. |
| rm -r [pasta] | Exclui uma pasta e todo o seu conteúdo permanentemente. |

# Explicação detalhada dos Comandos Básicos do Linux

## O Perigo Silencioso do Terminal
No ambiente gráfico, quando você faz algo perigoso, uma janela pula perguntando: "Tem certeza?". O terminal Linux assume que você é um profissional e sabe o que está fazendo. Por isso, ao digitar "rm arquivo.txt", o sistema apaga na hora, sem confirmar. Um erro de digitação no comando "rm -rf" (remover forçado recursivo) pode destruir o sistema inteiro em segundos. A regra de ouro é: leia duas vezes antes de apertar a tecla Enter.

## A diferença entre Copiar e Mover
Ao usar "cp", você fica com dois arquivos que gastam o dobro de espaço no disco. Ao usar "mv" para outra pasta do mesmo disco, o arquivo não muda fisicamente de lugar no disco rígido; o sistema apenas atualiza o "endereço" dele no índice, o que torna a operação de mover instantânea, mesmo para arquivos gigantes.

## 🔹 Recursos úteis
- [Linux Command](http://linuxcommand.org)
- [The Linux Kernel Archives](https://kernel.org)
- [The GNU Operating System](https://gnu.org)

---

# 🔹 Capítulo 3 – Gerenciamento de Pacotes (Instalando Programas)

## 🔹 Tópicos
- Introdução
- O que é um Gerenciador de Pacotes?
- Repositórios de Software
- O comando apt
- Atualizando a lista de programas
- Instalando e removendo programas

## 🔹 Subtópicos

### Introdução
Instalar programas no Linux é diferente de baixar um arquivo .exe no Windows. Aqui, utilizamos ferramentas super seguras que baixam aplicativos de servidores oficiais. Neste capítulo, você aprenderá como transformar o seu terminal em uma "App Store" poderosa.

### O que é um Gerenciador de Pacotes?
Um programa nunca trabalha sozinho; ele precisa de "dependências" (pequenos arquivos de código extra) para funcionar. O **Gerenciador de Pacotes** é um sistema inteligente que, quando você pede para instalar um programa, descobre todas essas dependências, baixa e instala tudo na ordem certa automaticamente. O curso foca nos sistemas Debian/Ubuntu, que usam o **apt**.

### Repositórios de Software
Repositórios são grandes servidores oficiais mantidos na internet pela comunidade Linux. Em vez de você caçar programas no Google, o seu Linux tem uma "lista telefônica" contendo o nome e o link de milhares de programas seguros testados e aprovados para a sua versão do sistema.

### O comando apt
O **Advanced Package Tool (apt)** é o comando que você usará para conversar com os repositórios. Com ele, você pede instalações, atualizações e desinstalações.

### Atualizando a lista de programas
Antes de instalar qualquer coisa, você precisa garantir que a sua "lista telefônica" local esteja sincronizada com os servidores da internet, para garantir que você fará o download das versões mais recentes. Fazemos isso atualizando (update) os índices.

```bash
sudo apt update
```

### Instalando e removendo programas
Uma vez que a lista está atualizada, a instalação é muito direta. Basta dizer ao apt o que você quer instalar. O mesmo vale para remover um software que você não usa mais.

```bash
sudo apt install htop
```

# 🔹 Conteúdo

Neste capítulo, aprendi o jeito Linux de gerenciar softwares. Entendi o conceito brilhante de Repositórios e Gerenciadores de Pacotes, que me livram de buscar programas na internet e de lidar com dependências quebradas. Aprendi a usar a ferramenta APT (focada em sistemas Ubuntu/Debian). O primeiro passo que gravei foi a importância de sempre rodar o "apt update" para sincronizar a minha lista de programas com a internet antes de fazer qualquer coisa. Em seguida, vi como é fácil e rápido instalar e remover aplicativos do sistema usando apenas uma linha de comando com o "apt install" e "apt remove".

# Comandos do Capítulo

| Comando | Descrição |
|---------------|-----------|
| apt update | Atualiza a lista interna de pacotes disponíveis e suas versões (não instala nada, apenas atualiza a lista). |
| apt upgrade | Baixa e instala as atualizações de todos os programas que já estão instalados no seu computador. |
| apt install [programa] | Baixa um novo programa e suas dependências, e o instala no sistema. |
| apt remove [programa] | Desinstala um programa do sistema. |
| apt autoremove | Remove pacotes "órfãos", ou seja, dependências que foram instaladas para um programa que você já excluiu e que não servem mais para nada. |

# Explicação detalhada dos Comandos Básicos do Linux

## Update vs Upgrade
Essa é a maior confusão para iniciantes. 
"Update" significa: "Ei sistema, pergunte aos servidores na internet quais são os programas e as versões mais novas que existem e apenas atualize a minha lista de anotações aqui".
"Upgrade" significa: "Agora que sua lista de anotações está atualizada, compare ela com o que eu tenho instalado no meu PC e faça o download/instalação das novas versões".
Sempre se roda o update antes do upgrade.

## 🔹 Recursos úteis
- [Linux Command](http://linuxcommand.org)
- [The Linux Kernel Archives](https://kernel.org)
- [The GNU Operating System](https://gnu.org)

---

# 🔹 Capítulo 4 – Permissões e Usuários

## 🔹 Tópicos
- Introdução
- O Usuário Root e o comando Sudo
- O modelo de Dono, Grupo e Outros
- Leitura, Escrita e Execução
- Alterando permissões (chmod)
- Alterando o dono do arquivo (chown)

## 🔹 Subtópicos

### Introdução
O Linux é um sistema "multi-usuário", o que significa que várias pessoas podem usar o mesmo computador (até ao mesmo tempo). Para evitar que um usuário apague o arquivo do outro, o Linux tem um sistema rigoroso de permissões e hierarquias que você aprenderá agora.

### O Usuário Root e o comando Sudo
O **Root** é o "Deus" do sistema Linux. É o usuário administrador supremo que pode apagar, instalar e destruir qualquer coisa. Usar o computador o tempo todo logado como Root é perigoso. Por isso usamos usuários normais, e quando precisamos de poder divino por alguns segundos (como para instalar um programa), usamos o comando **sudo** (Super User DO - Fazer como super usuário) antes do comando principal. Ele pedirá a sua senha para confirmar.

```bash
sudo apt update
```

### O modelo de Dono, Grupo e Outros
No Linux, todo arquivo possui três níveis de relacionamento:
- **User (Dono):** A pessoa que criou o arquivo.
- **Group (Grupo):** Um grupo de usuários que pode ter acesso compartilhado (ex: grupo "financeiro").
- **Others (Outros):** O resto do mundo; qualquer pessoa que tenha acesso ao computador, mas que não seja o dono nem faça parte do grupo.

### Leitura, Escrita e Execução
Para cada um dos três níveis acima, você pode dar ou tirar três tipos de acesso:
- **Read (r - Leitura):** Permite ver o que tem dentro.
- **Write (w - Escrita):** Permite modificar ou apagar.
- **Execute (x - Execução):** Permite rodar o arquivo como se fosse um programa.

### Alterando permissões (chmod)
O comando "chmod" (change mode) altera essas permissões. A forma mais fácil de entender o chmod é através da sua lógica matemática.
Leitura vale **4**, Escrita vale **2** e Execução vale **1**.
Se você quer dar Leitura e Escrita para o Dono, você soma 4+2 = 6. 
Você compõe três números (um para o dono, um para o grupo e um para outros). Por exemplo, "777" dá poder total (4+2+1=7) para todo mundo (Dono, Grupo, Outros), o que é péssimo para segurança.

```bash
chmod 755 meuarquivo.sh
```

### Alterando o dono do arquivo (chown)
O "chown" (change owner) serve para transferir a propriedade de um arquivo para outra pessoa. É muito usado quando você cria um arquivo como Root e precisa entregá-lo para um usuário comum.

```bash
sudo chown maria relatorio.txt
```

# 🔹 Conteúdo

Neste capítulo, mergulhei na segurança essencial do Linux. Compreendi que o Root tem poder absoluto e que devo invocar o "sudo" com sabedoria quando precisar de privilégios de administrador. Aprendi como o sistema classifica quem acessa um arquivo (Dono, Grupo e Outros) e os três poderes mágicos que posso conceder: ler, escrever e executar. Achei incrível a matemática por trás do chmod, onde somo os valores 4, 2 e 1 para criar as regras de acesso (como o famoso 755 ou o perigoso 777). Finalmente, vi como usar o chown para dar arquivos para outros usuários.

# Comandos do Capítulo

| Comando | Descrição |
|---------------|-----------|
| sudo [comando] | Executa qualquer comando temporariamente com permissão máxima de administrador. |
| chmod [numero] [arquivo] | Altera as permissões de leitura, escrita e execução do arquivo. |
| chown [usuario] [arquivo] | Altera quem é o dono oficial do arquivo. |
| su - | Troca o usuário atual permanentemente para a conta Root (exige a senha do Root). |
| exit | Sai do usuário atual e retorna para o usuário anterior ou fecha o terminal. |

# Explicação detalhada dos Comandos Básicos do Linux

## A Matemática do CHMOD (Notação Octal)
Quando vemos permissões como "644" ou "755", estamos olhando para três dígitos.
**Dígito 1:** Aplica-se ao Dono.
**Dígito 2:** Aplica-se ao Grupo.
**Dígito 3:** Aplica-se a Outros.
Os valores base são: r=4, w=2, x=1.
Um chmod **644**:
Dono recebe 6 (4+2) = Pode ler e escrever.
Grupo recebe 4 (4) = Só pode ler.
Outros recebe 4 (4) = Só pode ler.
Um chmod **755**:
Dono recebe 7 (4+2+1) = Pode ler, escrever e executar (rodar scripts).
Grupo e Outros recebem 5 (4+1) = Podem ler e executar, mas não alterar.

## 🔹 Recursos úteis
- [Linux Command](http://linuxcommand.org)
- [The Linux Kernel Archives](https://kernel.org)
- [The GNU Operating System](https://gnu.org)

---

# 🔹 Capítulo 5 – Edição de Texto no Terminal (O editor vi/vim)

## 🔹 Tópicos
- Introdução
- O que é o VI?
- A diferença entre o Modo de Comando e o Modo de Inserção
- Entrando e Saindo do modo de edição
- Salvando o arquivo e fechando o editor

## 🔹 Subtópicos

### Introdução
Existem momentos em que o sistema trava ou você está administrando um servidor na nuvem (sem interface gráfica) e precisa editar um arquivo de configuração com urgência. Não haverá Bloco de Notas ou Word. Você precisará usar um editor de texto de terminal. Aqui você conhecerá o mais famoso deles.

### O que é o VI?
O **vi** (ou sua versão melhorada, o **vim**) é um editor de texto que vem instalado por padrão em praticamente 100% dos sistemas Linux do mundo. Ele é incrivelmente poderoso e focado totalmente em quem não quer tirar as mãos do teclado para usar o mouse. 

```bash
vi arquivo.txt
```

### A diferença entre o Modo de Comando e o Modo de Inserção
Esse é o maior choque para iniciantes: quando você abre o vi e começa a digitar, o texto não vai para a tela. Isso ocorre porque o vi possui "modos".
Ele abre no **Modo de Comando**. Nesse modo, cada tecla que você aperta serve para dar uma ordem (ex: apertar 'x' deleta uma letra, apertar 'u' desfaz uma ação). 
Para conseguir escrever um texto de fato, você precisa passar para o **Modo de Inserção**.

### Entrando e Saindo do modo de edição
Para começar a escrever, pressione a letra **i** (de Insert) no seu teclado. O terminal mostrará "-- INSERT --" no canto inferior da tela. Agora você pode digitar normalmente.
Quando terminar de escrever e quiser salvar, você precisa voltar ao Modo de Comando. Para fazer isso, aperte a tecla **ESC**. A palavra "-- INSERT --" vai sumir.

### Salvando o arquivo e fechando o editor
Uma vez de volta ao Modo de Comando (pressionando ESC), você digita comandos que começam com dois pontos **:** para interagir com o arquivo.
- **:w** (write) -> Salva o arquivo.
- **:q** (quit) -> Sai do editor.
- **:wq** -> Salva e sai do editor ao mesmo tempo.
- **:q!** -> Sai forçado, descartando qualquer alteração que você fez (muito útil se errar algo e quiser fugir sem estragar nada).

# 🔹 Conteúdo

Neste capítulo, enfrentei um dos maiores ritos de passagem do Linux: aprender a usar o editor de texto vi. Descobri que ele não é um editor comum, e sim uma ferramenta que trabalha com Modos. Entendi que ele sempre inicia no Modo de Comando e que preciso apertar a tecla "i" para entrar no Modo de Inserção, sendo o único lugar onde posso realmente escrever um texto. Aprendi que para parar de escrever devo sempre apertar "ESC" e que salvar não é um atalho como Ctrl+S, mas sim o uso de comandos literais com dois pontos, como :wq para salvar e sair, ou :q! para fechar tudo em segurança sem alterar nada se eu cometer algum erro de digitação crítico.

# Comandos do Capítulo

| Comando (dentro do VI) | Descrição |
|---------------|-----------|
| vi [arquivo] | Abre o arquivo no editor de texto vi (feito no terminal, fora do editor). |
| i | Pressionado no Modo Comando: entra no Modo de Inserção para digitar texto. |
| ESC | Pressionado no Modo de Inserção: volta para o Modo de Comando. |
| :w | Salva as modificações no arquivo. |
| :q | Fecha o arquivo (se houver alterações não salvas, ele impedirá o fechamento). |
| :wq | Salva o arquivo e fecha tudo com sucesso. |
| :q! | Fecha o arquivo forçadamente e perde tudo o que foi feito desde o último salvamento. |
| x | (No Modo de Comando) Deleta a letra em cima do cursor. |
| dd | (No Modo de Comando) Deleta a linha inteira em que o cursor se encontra. |
| u | (No Modo de Comando) Desfaz a última ação (Undo). |

# Explicação detalhada dos Comandos Básicos do Linux

## O Trauma do "Como saio do Vim?"
Uma das piadas mais recorrentes na internet é que pessoas reiniciam seus computadores porque não conseguem sair do vi/vim. Isso acontece porque tentam usar atalhos como Ctrl+C, Ctrl+X ou a tecla Delete, e o programa começa a inserir caracteres estranhos na tela, travando o usuário. Lembre-se sempre do "Caminho Dourado do Resgate" no vim:
1. Aperte **ESC** três vezes (para ter absoluta certeza que você saiu de qualquer modo maluco e voltou para o Modo de Comando).
2. Digite **:q!** 3. Aperte **Enter**. Você estará salvo de volta no seu terminal amigável.

## 🔹 Recursos úteis
- [Linux Command](http://linuxcommand.org)
- [The Linux Kernel Archives](https://kernel.org)
- [The GNU Operating System](https://gnu.org)

---

# 🔹 Capítulo 6 – Introdução ao Shell Script (Criando Rotinas)

## 🔹 Tópicos
- Introdução
- O que é um Shell Script?
- A anatomia de um Script (A Shebang)
- Variáveis no Bash
- Laços de Repetição (for)
- Tomada de Decisão (if)

## 🔹 Subtópicos

### Introdução
Você já aprendeu a dar dezenas de ordens soltas no terminal. Mas e se você tivesse que fazer backup de 50 pastas todos os dias às 18h? Fazer isso na mão seria exaustivo. Aqui entra o **Shell Script**, a arte de colocar todos esses comandos dentro de um arquivo de texto e pedir para o Linux executar todos de uma só vez, automatizando o seu trabalho.

### O que é um Shell Script?
Um shell script nada mais é do que um arquivo de texto comum, com a extensão ".sh", que contém uma sequência de comandos do terminal e estruturas lógicas de programação. O sistema lê o arquivo de cima para baixo e executa comando por comando em alta velocidade.

### A anatomia de um Script (A Shebang)
Para criar um script, usamos o touch para criar um arquivo "meuscript.sh", usamos o chmod para dar a ele permissão de execução (ex: chmod +x meuscript.sh) e abrimos no editor vi. 
A primeira linha do script deve OBRIGATORIAMENTE ser a **Shebang**, que é o símbolo #! seguido do caminho do tradutor bash. Isso diz ao sistema quem deve ler aquele código.

```bash
#!/bin/bash
echo "Meu primeiro script"
```

Para executar o script recém criado, você deve chamar ele na pasta atual com um ponto e uma barra na frente.

```bash
./meuscript.sh
```

### Variáveis no Bash
Variáveis são como caixas que guardam informações para usarmos depois. Para criar uma variável, damos um nome a ela e usamos o sinal de igual sem espaços. Para usar o que está dentro da variável, colocamos um cifrão **$** na frente do nome.

```bash
NOME="Maria"
echo "O nome guardado é $NOME"
```

### Laços de Repetição (for)
A grande força da automação está na repetição de tarefas. O comando "for" (Para) diz: "Para cada item em uma lista, faça esta ação".

```bash
for NUMERO in 1 2 3
do
  echo "O número atual é $NUMERO"
done
```

### Tomada de Decisão (if)
Você também pode fazer o seu script tomar decisões baseadas em condições matemáticas ou textos. O "if" (Se) avalia uma condição, "then" (Então) executa a ação, e o "fi" encerra a verificação.

```bash
IDADE=18
if [ $IDADE -ge 18 ]; then
  echo "Você é maior de idade."
fi
```

# 🔹 Conteúdo

Neste capítulo, eu passei de um simples digitador de comandos para um programador básico do terminal. Descobri o poder do Shell Script, onde posso automatizar minhas tarefas criando arquivos ".sh". Aprendi que o passo fundamental para o script funcionar é iniciá-lo com a mágica "Shebang" (#!/bin/bash) e dar a ele permissões de execução com o chmod. Mergulhei nos fundamentos da programação criando variáveis com letras maiúsculas para guardar dados temporários, usando laços "for" para não ter que repetir comandos inúmeras vezes e estruturando regras inteligentes com o "if", garantindo que meu computador tome as decisões certas de forma totalmente automática.

# Comandos do Capítulo

| Estrutura | Descrição |
|---------------|-----------|
| #!/bin/bash | A Shebang: obrigatoriamente a primeira linha de qualquer shell script no Linux. |
| echo [texto] | Imprime uma mensagem ou o conteúdo de variáveis na tela do terminal. |
| ./[script.sh] | Comando para executar um script na pasta atual. |
| VAR="texto" | Criação de uma variável (não pode haver espaços antes ou depois do sinal de igual). |
| $VAR | Forma de chamar/invocar o conteúdo armazenado dentro da variável. |
| for / do / done | Estrutura de laço de repetição. |
| if / then / fi | Estrutura de condição para tomada de decisões lógicas. |
| -eq / -ge | Operadores lógicos dentro do 'if' (eq = igual a / ge = maior ou igual a). |

# Explicação detalhada dos Comandos Básicos do Linux

## O mistério do "./" na execução do script
Você pode se perguntar: "Por que eu digito só 'ls' para listar, mas preciso digitar './meuscript.sh' para rodar meu script?".
Isso é uma medida de segurança do Linux. Quando você digita um comando puro, o sistema procura nos diretórios de segurança oficiais. Como o seu script acabou de ser criado e está numa pasta pessoal comum, o Linux por padrão não confia nele e não o acha automaticamente. O ponto (.) significa "na pasta onde estou agora" e a barra (/) separa o diretório do arquivo. Portanto, "./meuscript.sh" significa literalmente: "Ignore os diretórios oficiais; confie e rode o programa que está exatamente dentro desta pasta em que me encontro".

## 🔹 Recursos úteis
- [Linux Command](http://linuxcommand.org)
- [The Linux Kernel Archives](https://kernel.org)
- [The GNU Operating System](https://gnu.org)