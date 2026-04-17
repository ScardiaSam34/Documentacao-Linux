# 🔹 Capítulo 3 – Linux Basics and System Startup

## 🔹 Tópicos
- Introdução
- Processo de boot
- Kernel, init e serviços
- Fundamentos do filesystem Linux
- Instalação de distribuições Linux

---

## 🔹 Subtópicos

### Introdução
Este capítulo apresenta conceitos fundamentais sobre o funcionamento interno do sistema Linux.  
São abordados temas como o processo de inicialização do sistema (boot), o papel do kernel, a organização do sistema de arquivos e os conceitos básicos envolvidos na instalação de uma distribuição Linux.

---

### Processo de Boot

Quando um computador com Linux é ligado, ele passa por uma sequência de etapas chamada **boot process**.  
Esse processo é responsável por preparar o hardware, carregar o sistema operacional e iniciar os serviços necessários para que o sistema funcione corretamente.

As etapas principais do boot incluem:

- inicialização do hardware
- carregamento do bootloader
- carregamento do kernel
- inicialização dos serviços do sistema

Esse processo garante que o sistema operacional seja carregado corretamente e esteja pronto para uso.

---

### Kernel, init e Services

Durante o processo de inicialização, três componentes importantes entram em ação.

**Kernel**  
O kernel é o núcleo do sistema operacional. Ele é responsável por gerenciar recursos do sistema, como:

- memória
- processos
- dispositivos de hardware
- comunicação entre software e hardware

**init (ou systemd)**  
Após o kernel ser carregado, ele inicia um processo chamado **init**, que é responsável por iniciar os serviços do sistema.  
Em muitas distribuições modernas, o init foi substituído pelo **systemd**.

**Services**  
Os serviços são programas executados em segundo plano que permitem o funcionamento de diversas funcionalidades do sistema, como:

- rede
- login de usuários
- servidores
- tarefas automáticas

---

### Fundamentos do Filesystem Linux

#### Linux Filesystems
O **filesystem** é a estrutura utilizada pelo sistema operacional para organizar e armazenar arquivos no disco.

No Linux, o filesystem organiza dados de forma hierárquica, semelhante a uma árvore de diretórios.

---

#### Partitions and Filesystems
Um disco rígido pode ser dividido em **partições**.  
Cada partição pode conter um filesystem diferente.

Isso permite organizar melhor o armazenamento do sistema e separar diferentes tipos de dados.

---

#### The Filesystem Hierarchy Standard (FHS)
O **Filesystem Hierarchy Standard (FHS)** define uma estrutura padrão para a organização dos diretórios no Linux.

Essa padronização facilita o uso do sistema, pois os arquivos e programas ficam organizados em locais previsíveis.

Alguns diretórios importantes incluem:

- `/` → diretório raiz do sistema
- `/home` → arquivos pessoais dos usuários
- `/etc` → arquivos de configuração do sistema
- `/var` → arquivos que mudam com frequência
- `/bin` → comandos essenciais do sistema

---

#### Mais sobre o Filesystem Hierarchy Standard
Seguir o padrão FHS ajuda a manter o sistema organizado e facilita a administração do Linux, pois os administradores sabem onde encontrar configurações, programas e arquivos importantes.

---

#### Visualizando o filesystem pela interface gráfica
Além da linha de comando (CLI), o filesystem também pode ser explorado utilizando interfaces gráficas (GUI), como gerenciadores de arquivos presentes em ambientes gráficos do Linux.

Essas interfaces permitem navegar entre diretórios e visualizar arquivos de forma semelhante a outros sistemas operacionais.

---

### Instalação de distribuições Linux

#### Escolhendo uma distribuição Linux
Existem muitas distribuições Linux disponíveis, cada uma voltada para diferentes tipos de usuários e necessidades.

Algumas distribuições são focadas em iniciantes, enquanto outras são voltadas para servidores, desenvolvimento ou ambientes corporativos.

---

#### Perguntas ao escolher uma distribuição
Ao escolher uma distribuição Linux, é importante considerar fatores como:

- facilidade de uso
- suporte da comunidade
- compatibilidade com hardware
- disponibilidade de software
- objetivo de uso (desktop, servidor, estudo, etc.)

---

#### Instalação do Linux
A instalação de uma distribuição Linux normalmente envolve:

- escolher a distribuição
- preparar a mídia de instalação
- configurar partições
- selecionar pacotes e configurações do sistema
- criar usuários

Após a instalação, o sistema estará pronto para ser utilizado.

---

#### Passos para instalar Ubuntu
A instalação do **Ubuntu** geralmente inclui:

1. iniciar o sistema pela mídia de instalação
2. escolher idioma e configurações básicas
3. selecionar o tipo de instalação
4. configurar disco e partições
5. criar usuário e senha
6. finalizar a instalação

---

#### Passos para instalar CentOS
O processo de instalação do **CentOS** segue uma lógica semelhante:

1. iniciar pela mídia de instalação
2. configurar idioma e layout do teclado
3. configurar rede e disco
4. selecionar pacotes de instalação
5. criar usuário e senha
6. concluir a instalação do sistema

---

## 🔹 Conteúdo

Neste capítulo aprendi sobre alguns conceitos básicos do funcionamento interno do Linux, principalmente relacionados ao processo de inicialização do sistema e à organização dos arquivos.

Primeiro entendi como funciona o **boot process**, que é a sequência de etapas que ocorre quando o computador é ligado. Durante esse processo o hardware é inicializado, o bootloader carrega o sistema operacional e o kernel é executado para iniciar o funcionamento do sistema.

Também aprendi sobre o papel do **kernel**, que é o núcleo do sistema operacional. Ele é responsável por gerenciar recursos importantes do computador, como memória, processos e dispositivos de hardware. Após o kernel ser carregado, o sistema inicia o processo **init** (ou systemd nas distribuições mais modernas), que é responsável por iniciar os serviços necessários para o funcionamento do sistema.

Outro conceito importante foi o **filesystem Linux**, que define como os arquivos são organizados no sistema. No Linux os arquivos são organizados em uma estrutura hierárquica que começa no diretório raiz `/`. Dentro dessa estrutura existem diretórios específicos para diferentes tipos de arquivos, como arquivos de usuários, configurações do sistema e programas.

Também aprendi sobre o **Filesystem Hierarchy Standard (FHS)**, que define um padrão para a organização dos diretórios no Linux. Esse padrão facilita a administração do sistema, pois mantém os arquivos organizados de forma previsível.

Por fim, o capítulo explicou alguns conceitos sobre a **instalação de distribuições Linux**. Existem várias distribuições disponíveis, e a escolha depende das necessidades do usuário. Durante a instalação é necessário configurar algumas opções básicas, como idioma, disco, usuários e pacotes do sistema.

## 🔹 Recursos úteis
https://kernel.org  
https://linuxfoundation.org  
https://ubuntu.com  
https://centos.org