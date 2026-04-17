# Capítulo 10 — Sistema de Arquivos no Linux

## Estrutura em Árvore

Recapitulando, a organização dos dados segue uma estrutura padronizada em forma de árvore, iniciando sempre no diretório **raiz** `/`. Esse diretório representa o ponto mais alto do sistema, e todos os outros diretórios e arquivos estão organizados a partir dele. Diferente de outros sistemas operacionais que utilizam múltiplas unidades (como C: ou D:), **no Linux tudo faz parte de uma única hierarquia contínua.**

## FHS — Padrão de Organização

Essa estrutura segue o padrão **FHS (Filesystem Hierarchy Standard)**, que define a função de cada diretório. Isso garante organização e consistência no sistema.

Principais diretórios:

- `/home` → armazena os arquivos pessoais dos usuários  
- `/etc` → contém arquivos de configuração  
- `/var` → guarda dados que mudam com frequência, como logs  
- `/boot` → possui arquivos necessários para inicialização do sistema  
- `/root` → diretório pessoal do administrador  

## Partições e Montagem

O armazenamento físico no Linux é dividido em **partições**, que são seções do disco rígido. Cada partição pode ter seu próprio sistema de arquivos e pode ser usada separadamente. Para que uma partição seja acessível, ela precisa ser **montada**, ou seja, conectada a algum ponto da árvore de diretórios. Quando uma partição é montada, seu conteúdo passa a aparecer dentro do diretório escolhido, integrando-se ao sistema. Esse processo pode ser feito manualmente com o comando `mount`, ou automaticamente durante a inicialização do sistema por meio do arquivo `/etc/fstab`, que define quais sistemas de arquivos devem ser montados no boot.

## Pseudo-sistemas de Arquivos

Nem todos os sistemas de arquivos existem fisicamente no disco. Alguns são chamados de **pseudo-sistemas de arquivos**, pois existem apenas na memória e fornecem informações sobre o funcionamento do sistema. Um exemplo importante é o diretório `/proc`, que contém dados em tempo real sobre o sistema e os processos em execução.

## Compartilhamento de Arquivos (NFS)

O Linux também permite o compartilhamento de arquivos pela rede usando o **NFS (Network File System)**. Com ele, diretórios de um computador podem ser acessados por outro como se fossem locais, sendo muito utilizado em ambientes corporativos e servidores.

## Manipulação de Arquivos

Para manipular arquivos, o Linux oferece diversas ferramentas. O comando `cp` permite copiar arquivos de forma simples, enquanto o `rsync` é mais avançado, pois copia apenas as alterações, economizando tempo e recursos, especialmente em transferências pela rede.

## Compactação de Arquivos

Na compactação de arquivos, existem vários formatos disponíveis, como `gzip`, `bzip2`, `xz` e `zip`. Cada um possui características diferentes em termos de velocidade e nível de compressão. O comando `tar` é frequentemente utilizado para agrupar vários arquivos em um único pacote, podendo também aplicar compressão.

## Cópia em Nível Bruto

Além disso, o comando `dd` permite copiar dados em nível bruto, sendo usado para clonar discos inteiros ou criar backups completos. No entanto, seu uso exige muito cuidado, pois qualquer erro pode resultar na perda total de dados.

## Aplicação de Patches

Outro recurso importante é o comando `patch`, utilizado para aplicar modificações em arquivos a partir de diferenças previamente definidas, muito comum no desenvolvimento de software.

## Identificação de Arquivos

Um detalhe essencial no Linux é que a extensão de um arquivo não determina seu tipo. Ou seja, um arquivo não precisa terminar com `.txt` ou `.exe` para ser reconhecido. Para identificar o tipo real de um arquivo, utiliza-se o comando `file`, que analisa seu conteúdo.