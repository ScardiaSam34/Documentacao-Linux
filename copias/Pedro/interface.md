# Interface da máquina e operações pós boot 🖥️

## Gerenciador de display
É o responsável por gerenciar o display de forma geral, por exemplo:
- Gerenciamento dos logins gráficos
- Carrega a GUI

## Ambiente desktop 💻
Consiste da junção dum gerente de sessão (que inicia e mantém os componentes da sessão gráfica) e um gerenciador de janela (que controla a posição e movimentação das janelas, barras de nome e controles)

##  GNOME 
É o ambiente desktop mais comumente utilizado dentro das distribuições Linux e é muito semelhante de forma visual ao Windows, sendo muito usado como um ambiente de transição Windos -> Linux.

Possui algumas "extensões" que podem ser baixadas para aumentar ainda mais a personalização visual do seu ambiente desktop, uma das mas usadas e conhecidas, é o **gnome-tweaks**

## Network Time Protocol (NTP) 🕑
É um protocolo e uma ferramenta muito usada no Linux, e é o recurso mais confiável para a definição do horário da máquina, usando de alguns servidores da internet para ver o horário local de diferentes partes do globo.

## Gerenciador de pacotes 📦
Permite o usuário instalar, atualizar, remover, construir e gerenciar pacotes - e além disso - gerenciadores de pacotes mais atuais também cuidam das dependências dos pacotes e programas instalados

### Principais gerenciadores de pacotes
- **dpkg:** versão mais "anterior/antiga" do **apt**, é principalmente usado em sistemas Debian mais antigos ou menos atualizados e não resolve as dependências de seus pacotes.
- **apt:** gerenciador de pacotes mais usados nas distros atuais do Linux, resolve as dependências dos pacotes e aplicativos instalados e tem sua origem no comando **apt-get**