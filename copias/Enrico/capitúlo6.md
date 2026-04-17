## Capitúlo 06.
Neste capitúlo vemos que para personalização das configurações do dispositivo é bem simples pela interface gráfica. O Linux usa um sistema de chamado "Coordinated Universal Time" (UTC) pára seu próprio sistema interno de tempo, que também pode ser configurado, além de outras ferramentas como dpkg (Debian Package) que é fundamental para gerenciar pacotes .deb em sistemas Debian, Ubuntu, Kali Linux e derivados, RPM que também gerencia pacotes porém para os sistemas Red Hat, como RHEL, CentOS, Fedora e SUSE

Configurações de Sistema e Hardware
O Linux oferece controle total sobre como o hardware interage com o usuário através de painéis centralizados:

Painel de Configurações: Centraliza as opções básicas de personalização e ajustes da área de trabalho.

Monitores: Permite ajustar a resolução da tela e gerenciar o uso de múltiplos monitores simultaneamente.

Rede (Network Manager): Gerencia conexões Wi-Fi, redes móveis, VPNs e senhas de forma simplificada.

Gerenciamento de Tempo
A precisão do relógio é fundamental para o funcionamento de logs e segurança do sistema:

Interno (UTC): O Linux utiliza internamente o Tempo Universal Coordenado para evitar conflitos de fuso horário.

Sincronização (NTP): O Network Time Protocol é o padrão para manter a hora do sistema sempre correta através de servidores na internet.

### Configurações e Pacotes

| Recurso | Descrição / Funcionamento | Ferramenta/Protocolo |
| :--- | :--- | :---: |
| **Ajustes Gerais** | Configurações básicas e personalização da área de trabalho | Painel de Configurações |
| **Tempo Interno** | Padrão mundial usado internamente pelo sistema Linux | **UTC** |
| **Sincronia de Hora** | Sincroniza a hora local via servidores de internet | **NTP** |
| **Vídeo** | Ajuste de resolução e gestão de múltiplas telas | Painel Monitores |
| **Conectividade** | Gestão de Wi-Fi, Banda Larga Móvel e VPNs | Gerenciador de Rede |
| **Base Debian** | Gerenciamento de pacotes para Debian, Ubuntu e derivados | **dpkg / APT** |
| **Base Red Hat** | Sistema usado por RHEL, CentOS, openSUSE e Oracle | **RPM** |
