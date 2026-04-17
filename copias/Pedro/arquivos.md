# Operações e Gerenciamento de Sistemas de Arquivos no Linux

## 1. Hierarquia e Layout do Filesystem (FHS)

O Linux utiliza o **Filesystem Hierarchy Standard (FHS)**. Diferente de outros sistemas, não há unidades de disco separadas por letras (C:, D:); tudo está sob o diretório raiz `/`.

### Diretórios Estratégicos e Seus Propósitos
* **`/` (Raiz):** O topo da hierarquia.
* **`/bin` e `/usr/bin`:** Comandos essenciais para todos os usuários (ex: `ls`, `cp`).
* **`/sbin` e `/usr/sbin`:** Binários de administração do sistema (ex: `fdisk`, `ip`).
* **`/etc`:** Arquivos de configuração local do sistema.
* **`/home`:** Diretórios pessoais dos usuários.
* **`/root`:** Diretório pessoal do superusuário.
* **`/var`:** Arquivos de dados variáveis (logs, spool de impressão, bancos de dados).
* **`/tmp`:** Arquivos temporários (frequentemente apagados no boot).
* **`/dev`:** Arquivos de dispositivos físicos e virtuais.
* **`/proc` e `/sys`:** Sistemas de arquivos virtuais que representam o kernel e o hardware em tempo real.

---

## 2. Tipos Comuns de Filesystem

Cada sistema de arquivos possui vantagens dependendo da carga de trabalho:

| Tipo | Descrição |
| :--- | :--- |
| **Ext4** | O padrão para a maioria das distribuições. Estável e performático. |
| **XFS** | Alta performance para arquivos grandes e paralelismo. Padrão no RHEL. |
| **Btrfs** | Suporta snapshots, compressão e gerenciamento de volumes nativos. |
| **ZFS** | Focado em integridade de dados e grandes volumes (comum em storages). |
| **Vfat / ExFAT** | Usados para compatibilidade com outros sistemas e pendrives. |

---

## 3. Partições, Montagem e Verificação

### Gerenciamento de Partições
Discos são identificados como arquivos em `/dev` (ex: `/dev/sda` para discos SATA/SCSI ou `/dev/nvme0n1` para NVMe).
* **Ferramentas:** `fdisk` (MBR), `gdisk` (GPT) ou `parted`.

### Montagem (Mounting)
Para acessar um sistema de arquivos, ele deve ser montado em um diretório:
* **Montar:** `mount /dev/sdb1 /mnt/dados`
* **Desmontar:** `umount /mnt/dados`
* **Persistência:** As montagens permanentes são configuradas no arquivo `/etc/fstab`.

### Verificação
* **`fsck`:** Utilizado para verificar e reparar erros no sistema de arquivos. Deve ser executado em partições **desmontadas**.

---

## 4. Network File System (NFS)

O NFS permite que diretórios sejam compartilhados através da rede como se fossem locais.

* **No Servidor:** Define-se os compartilhamentos no arquivo `/etc/exports`.
    * Exemplo: `/home/comum 192.168.1.0/24(rw,sync,no_root_squash)`
* **No Cliente:** Monta-se o recurso remoto:
    * `mount -t nfs 192.168.1.10:/home/comum /mnt/nfs_remoto`

---

## 5. Identificação e Comparação de Arquivos

### Identificar Tipos de Arquivo
O Linux não confia apenas na extensão (ex: .txt).
* **`file <arquivo>`:** Analisa o "magic number" do cabeçalho para dizer o que o arquivo realmente é.
* **`stat <arquivo>`:** Exibe detalhes de metadados (tamanho, permissões, datas de acesso/modificação).

### Comparar Arquivos
* **`diff <arq1> <arq2>`:** Mostra as diferenças linha por linha entre dois arquivos de texto.
* **`cmp <arq1> <arq2>`:** Útil para verificar se dois arquivos binários são idênticos byte a byte.
* **`md5sum` / `sha256sum`:** Gera hashes para verificar a integridade e se os arquivos são exatamente iguais.

---

## 6. Backups e Compressão de Dados

### Arquivamento e Backup
* **`tar` (Tape Archiver):** Agrupa vários arquivos em um só.
    * Criar: `tar -cvf backup.tar /diretorio`
    * Extrair: `tar -xvf backup.tar`

### Compressão
* **`gzip` / `gunzip`:** Compressão rápida (gera `.gz`).
* **`bzip2`:** Melhor compressão que o gzip, porém mais lento (gera `.bz2`).
* **`xz`:** Alta taxa de compressão, muito comum em pacotes de software (gera `.xz`).

### Comando Combinado (O mais comum)
* **Criar backup comprimido:** `tar -czvf backup.tar.gz /diretorio`
* **Extrair backup comprimido:** `tar -xzvf backup.tar.gz`