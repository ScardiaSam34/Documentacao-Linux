# 🔹 Capítulo 5 – System Configuration from the Graphical Interface

## 🔹 Tópicos
- Introdução
- Configurações do Sistema e GNOME Tweaks
- Configurações de Tela (Display (Displays Panel))
- Data e Hora (UTC e NTP)
- Network Manager (Wi-Fi, Mobile Broadband e VPNs)
- Instalação e Atualização de Software (dpkg, RPM e YaST)

---

## 🔹 Subtópicos

### Introdução
Este capítulo apresenta como realizar **configurações do sistema Linux utilizando a interface gráfica (GUI)**. Ele mostra como configurar aspectos importantes do sistema, como tela, data e hora, rede e instalação de software, utilizando ferramentas gráficas disponíveis nas distribuições Linux.

### Configurações do sistema

#### System Settings
As **System Settings (Configurações do Sistema)** são ferramentas gráficas utilizadas para configurar diferentes aspectos do sistema operacional. Através delas é possível modificar várias opções do sistema sem precisar utilizar comandos no terminal.

#### Menus de configuração
O menu de configurações do sistema permite acessar diferentes opções, como configurações de tela, rede, data e hora, dispositivos, contas de usuários e aparência do sistema. Essas configurações ajudam o usuário a personalizar e controlar o funcionamento do sistema.

#### gnome-tweaks
O **gnome-tweaks** é uma ferramenta utilizada para personalizar o ambiente gráfico GNOME. Ela permite modificar configurações avançadas da interface, como temas, comportamento das janelas, aparência do desktop e extensões do GNOME.

### Tela, Data e Hora

#### Configurações de tela (Display (Displays Panel))
O painel **Display (Displays Panel)** permite ajustar configurações da tela, sendo utilizado principalmente para **configurar a resolução da tela (Screen Resolution)** e gerenciar múltiplos monitores. (Questão 5.2)



#### Configurando múltiplos monitores
O Linux também permite utilizar **mais de um monitor ao mesmo tempo**. O usuário pode configurar a posição das telas, qual será a tela principal e escolher entre espelhamento ou extensão do desktop no painel Display.

#### Configurações de data e hora
O sistema permite configurar manualmente ou automaticamente a **data e hora** do computador a partir do painel System Settings. Um ponto fundamental é que o Linux sempre utiliza o **UTC (Coordinated Universal Time)** para a sua própria manutenção de tempo interna, convertendo para o fuso horário local apenas para a exibição ao usuário.

#### Network Time Protocol (NTP)
O **Network Time Protocol (NTP)** é o protocolo mais popular e confiável **utilizado para configurar a hora local através de servidores da internet**. (Questão 5.1) Isso garante maior precisão na hora do sistema, o que é vital para logs e conexões de rede.

### Network Manager

#### Configuração de rede
O **Network Manager** é a ferramenta gráfica utilizada para gerenciar conexões de rede no Linux. Ele pode apresentar redes sem fio disponíveis, permitir a escolha de conexões móveis, lidar com senhas e configurar VPNs.

#### Conexões com fio e sem fio
O sistema pode se conectar à rede utilizando **wired connection** (cabo Ethernet) ou **wireless connection** (Wi-Fi). Para conectar a uma rede Wi-Fi, o usuário precisa selecionar a rede disponível, inserir a senha de acesso e confirmar a conexão. O sistema pode se conectar automaticamente no futuro.

#### Gerenciamento de rede
O Network Manager também permite ativar ou desativar conexões, visualizar informações da rede, configurar endereços IP e modificar configurações avançadas.

#### Conexões Mobile Broadband e VPN
O Linux suporta conexões **Mobile Broadband** (internet móvel) e **VPN (Virtual Private Network)**, utilizadas para conexões seguras em redes privadas. O Network Manager possui suporte integrado a diversas tecnologias de VPN, incluindo **OpenVPN, Cisco OpenConnect e IPSec**. (Questão 5.3)



### Instalação e atualização de software

#### Gerenciamento de software
As distribuições Linux utilizam **gerenciadores de pacotes** para instalar, atualizar e remover programas. Atualmente, **dpkg e RPM são os sistemas base de gerenciamento de pacotes** mais populares no Linux.

#### Debian Packaging e Ubuntu
Distribuições baseadas no Debian (como o próprio Debian e o Ubuntu) utilizam utilitários baseados em **dpkg** e pacotes no formato **.deb**. No caso do Ubuntu, as ferramentas de gerenciamento de pacotes utilizadas incluem o utilitário de linha de comando `dpkg` e o **Ubuntu Software Center**, que atua como uma interface gráfica para gerenciamento de pacotes baseada em dpkg. (Questão 5.4)

#### Red Hat Package Manager (RPM)
O sistema **RPM** foi desenvolvido pela Red Hat e adotado por várias outras distribuições, incluindo openSUSE, Mandriva, CentOS e Oracle Linux. Ele permite instalar, atualizar e remover programas de forma organizada.

#### openSUSE YaST Software Management
O openSUSE utiliza a ferramenta **YaST software management** para adicionar e remover pacotes de software de forma centralizada. (Questão 5.5)



#### Instalação de software no Linux
Dependendo da distribuição, o usuário pode instalar programas utilizando gerenciadores gráficos de software, centros de aplicativos ou ferramentas de gerenciamento de pacotes.

---

# 🔹 Conteúdo

Neste capítulo, aprendi como configurar o sistema Linux diretamente pela interface gráfica, sem a necessidade de recorrer ao terminal. Comecei explorando o painel de **System Settings**, onde pude entender como o menu de **Display** é a ferramenta correta para ajustar a resolução da tela e organizar múltiplos monitores. Também descobri a importância do **gnome-tweaks** para personalizar detalhes mais profundos da interface.

Na parte de relógio e fuso horário, compreendi um conceito técnico fundamental: o Linux utiliza o **UTC** para seu controle interno de tempo, independentemente de onde eu esteja. Aprendi também que o **NTP (Network Time Protocol)** é o protocolo padrão responsável por manter a hora do meu computador sempre perfeitamente sincronizada com servidores da internet.

Explorei o **Network Manager** e percebi o quão robusto ele é. Além de gerenciar redes Wi-Fi e Mobile Broadband com facilidade, ele possui suporte integrado para configurar conexões seguras corporativas utilizando tecnologias como **OpenVPN, Cisco OpenConnect e IPSec**.

Por fim, desmistifiquei a instalação de softwares no Linux, entendendo que o ecossistema é dividido principalmente em duas grandes famílias que utilizam sistemas base: **dpkg** (usado pelo Debian e Ubuntu, contando com o Ubuntu Software Center como interface gráfica baseada nele) e o **RPM** (criado pela Red Hat e adotado por sistemas como o CentOS e o openSUSE). Entendi que distribuições corporativas possuem painéis próprios poderosos para essa tarefa, como é o caso do **YaST** no openSUSE.

---

# Conceitos e Ferramentas do Capítulo

| Ferramenta / Protocolo | Descrição |
| :--- | :--- |
| System Settings | Painel central para controle de configurações básicas do desktop. |
| Display (Displays Panel) | Utilizado para configurar a resolução de tela e múltiplos monitores (Questão 5.2). |
| NTP | Protocolo que sincroniza a hora local via servidores de internet (Questão 5.1). |
| Network Manager | Gerencia conexões Wi-Fi, redes móveis e VPNs corporativas (Questão 5.3). |
| dpkg | Sistema base de gerenciamento de pacotes para sistemas Debian/Ubuntu (Questão 5.4). |
| Ubuntu Software Center | Interface gráfica para gestão de pacotes baseada em dpkg no Ubuntu (Questão 5.4). |
| RPM | Sistema base de pacotes da Red Hat, usado também no CentOS e openSUSE. |
| YaST | Ferramenta gráfica do openSUSE para gestão de software e do sistema (Questão 5.5). |

---

# Explicação dos Conceitos Fundamentais

## O Relógio Interno (UTC vs Local Time)
O Linux lida com o tempo de forma muito inteligente. Em vez de salvar a hora local na placa-mãe (o que causa problemas com horário de verão e viagens), o sistema salva tudo em UTC (Tempo Universal Coordenado). O fuso horário do usuário é apenas um "filtro visual" aplicado sobre esse tempo absoluto. O protocolo NTP garante que esse relógio absoluto nunca atrase.

## O Poder do Network Manager em VPNs
Conectar-se a redes corporativas pelo terminal pode ser complexo devido aos certificados de segurança. O Network Manager simplifica isso integrando nativamente clientes como IPSec, OpenVPN e Cisco OpenConnect. Isso significa que o usuário não precisa instalar aplicativos de terceiros para trabalhar de casa com segurança; o próprio sistema operacional lida com a criptografia da rede de forma gráfica.

## A Camada Base dos Pacotes (dpkg e RPM)
É fundamental entender que `dpkg` e `RPM` são sistemas base. Eles lidam com a instalação dos arquivos em si, mas não resolvem dependências complexas sozinhos (função delegada a ferramentas como `apt` ou `dnf`). O Ubuntu Software Center, por exemplo, é uma interface amigável que "conversa" com essa base dpkg para facilitar a vida do usuário. Essa organização garante que o sistema permaneça íntegro ao instalar novos programas.

---

## 🔹 Recursos úteis
- https://www.gnome.org
- https://linuxfoundation.org
- https://opensource.org
- https://linuxcommand.org