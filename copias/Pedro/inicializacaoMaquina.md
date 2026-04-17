# Inicialização da máquina Linux 🖥️

A iniciação da máquina Linux, apesar de ser rápida graças a leveza e praticidade do seu sistema, é um processo extremamente complexo e completo que passa por diversas etapas. Sendo elas:

1. Máquina é ligada/recebe energia
2. Basic Input Output System (**BIOS**)
3. Master Boot Record (**MBR**) ou Partição *EFI*
4. Boot Loader
5. Kernel
6. Disco inicial *RAM* (**- initramfs**)
7. **/sbin/init**
8. Shell de Comando usa o **getty**
9. Interface Gráfica do Usuário (**GUI**)

## BIOS 
É responsável por reconhecer e iniciar todos os componentes, desde os físicos (*hardware*) até os virtuais (*software*). 

Também é responsável por reconhecer os dispositivos de entrada e saída conectados à sua máquina, para assim usa-los devidamente, e pela testagem da principal memória. E todo esse processo é chamado de **POST** (*Power On Self Test*)

##  MBR (Master Boot Record) e Boot Loader
Vai carregar os valores de tempo atríbuidos a cada componente da sua máquina usando do CMOS. Também é responsável por carregar o Kernel, o disco de RAM inicial e/ou o filesystem dentro da memória.

Grande parte dos Boot Loaders vão apresentar interfaces gráficas para que o usuário possa escolher diferentes tipos de inicialização, prevenindo que outros sistemas sejam possivelmente instalados de forma indesejada

## Disco inicial RAM 💽
A imagem do filesystem **initramfs** contém programas e arquivos binários que realizam todas as ações necessárias para montar a raiz do sistema de forma adequada, incluindo fornecer a funcionalidade do *Kernel* necessária para o filesystem específico que será usado e carregar os drivers de dispositivos para controle de armazenamento em massa. Depois que o filesystem é encontrado, ele é verificado em busca de erros e montado.

Depois que o processo de montagem e configuração do filesystem é completo, o initramfs é limpo da RAM e o comando init é executado na raiz

## /sbin/init
O **init**, de forma resumida, cuida da montagem e pivô para o filesystem root final. A maior parte dos sistemas traçam sua origem até o **init**, as únicas exceções são os processos Kernel, que são iniciados pelo mesmo para gerenciar detalhes internos do sistema operacional.

O **init** também é responsável por manter o sistema operacional funcionando e o desliga-lo de forma limpa. Uma de suas responsabilidades é atuar como gestor para todos os para todos os processos que não sejam Kernel.

## systemd
É um startup semelhante ao *init*, na realidade, ele é um startup que substitui o /sbin/init de uma forma muito mais eficiente. O systemd, diferentemente do init, ele possui processamento paralelo, permitindo que a inicialização da máquina seja ainda mais rápida. 

Os prompts e scripts complexos do init são trocados por arquivos de configuração mais simples que enumeram o que deve ser feito antes de se iniciar um serviço, como executa-lo/inicia-lo, e as condições que ele eve indicar que foram cumpridas quando a inicialização termina.

O systemd também possui alguns comandos possíveis, tendo como sua base o comando **systemctl**

### Usos do systemctl
Iniciar, parar ou reiniciar um serviço em um sistema em execução atual:

```
$ sudo systemctl start <nomeserviço>
$ sudo systemctl stop <nomeserviço>
$ sudo restart <nomeservico>
```

Habilitando ou desabilitando um serviço do sistema do sistema para iniciar junto com o boot do sistema:


```
$ sudo systemctl enable <nomeserviço>
$ sudo systemctl disable <nomeserviço>
```

Checar o estado de um serviço:

```
$ sudo systemctl status <nomeserviço>
```

## Filesystem (sistemas de arquivos) 🗂️
### Tipos de filesystems
#### Discos convencionais
- ext3
- ext4
- XFS
- Btrfs
- JFS
- NFTS
- vfat
- exfat

#### Armazenamento flash 
- ubifs
- jffs2
- yaffs

#### Filesystem de banco de dados
#### Filesystem com propósitos especiais
- procfs
- tmpfs
- squashfs
- debugfs
- fuse

### Partições
É basicamente uma parte física do disco onde a informação é armazenada. Um único filesystem pode usar mais de uma partição se usar de links simbólicos

### Padrão da hierarquia dos filesystems (FHS)
O **FHS** foi criado para facilitar a vida dos programadores e usuários do Linux, trazendo um padrão dentro do armazenamento do filesystem, mesmo entre distros diferentes

#### Características
- Usa '/' para separar caminhos entre pastas e/ou arquivos
- Não possui letras de unidade
- Diferentes drivers e/ou partições são montados como diretórios dentro de um único filesystem
- Mídias removíveis normalmente aparecerão como **/run/media/homeusuario/nomedisco**
- Todos os nomes de arquivos e de diretórios são case-sensitive