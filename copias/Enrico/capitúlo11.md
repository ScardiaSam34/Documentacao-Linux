## 11. Sistemas de Arquivos e Hierarquia (FHS)
 1. Estrutura e Hierarquia (FHS)

O Linux utiliza o Filesystem Hierarchy Standard (FHS) para organizar onde cada arquivo deve ficar. Tudo começa no diretório / (raiz).

- /boot: Contém o Kernel e os arquivos necessários para iniciar o computador (como o GRUB).

- /root: O diretório pessoal (home) exclusivo do superusuário (root). Não deve ser confundido com a   raiz /.

- /var: Armazena dados variáveis, como logs e bancos de dados. É recomendável colocá-lo em uma partição separada para que, se ele lotar, não trave o sistema operacional inteiro.

- /proc: Um pseudo-sistema de arquivos. Ele não ocupa espaço no disco; existe apenas na memória RAM e serve para o kernel comunicar informações sobre processos e hardware.

2. Discos, Partições e Montagem
  
    Diferente do Windows, onde os discos são letras (C:, D:), no Linux tudo é anexado à árvore principal.

- Montagem: O processo de ligar uma partição a um diretório é chamado de "montar".

- /etc/fstab: É o arquivo de configuração que diz ao Linux quais partições devem ser montadas automaticamente durante a inicialização.

- NFS (Network File System): Permite que diretórios em outros computadores na rede sejam montados localmente como se estivessem no seu próprio disco.

3. Ferramentas de Manipulação e Cópia

- O Linux oferece comandos poderosos para gerenciar dados, desde arquivos individuais até discos inteiros.

- cp vs rsync: Enquanto o cp faz cópias simples locais, o rsync é inteligente: ele sincroniza apenas as partes alteradas dos arquivos e funciona eficientemente através da rede.
 
- dd (Data Duplicator): Um utilitário de baixo nível que copia bit a bit. É usado para criar imagens ISO de pendrives ou fazer clones idênticos de partições inteiras.

- patch: Uma ferramenta que aplica alterações em arquivos de texto. Em vez de enviar um arquivo inteiro novo, desenvolvedores enviam um "arquivo de patch" que contém apenas o que mudou.

4. Compactação e Arquivamento
É comum confundir "agrupar" com "compactar". No Linux, geralmente fazemos os dois em etapas ou com comandos combinados.

- tar: Cria um "pacote" contendo vários arquivos (o famoso tarball). Por si só, o tar não compacta, ele apenas junta.

- Formatos de Compactação: gzip (rápido), bzip2 (melhor compressão) e xz (altíssima compressão, mas mais lento).

- Extensões: No Linux, as extensões (como .exe ou .jpg) são apenas informativas para o usuário. O sistema identifica o tipo do arquivo pelo seu conteúdo (números mágicos) e permissões.
