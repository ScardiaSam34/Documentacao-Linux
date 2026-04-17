# Capítulo 3 — Trabalhando com Arquivos, Diretórios e Inicialização (BIOS/UEFI)

No Linux, os arquivos e diretórios são organizados em uma estrutura hierárquica em forma de árvore, onde tudo começa a partir do diretório **raiz** `/`. Esse diretório é o ponto mais alto do sistema, e todos os outros diretórios e arquivos estão organizados dentro dele. Isso significa que, independentemente do que você estiver acessando seja um arquivo pessoal ou uma configuração do sistema tudo parte dessa estrutura única.

Os diretórios funcionam como organizadores de arquivos, e o sistema mantém um diretório atual de trabalho. Para saber em qual diretório você está, utiliza-se o comando:

```bash
pwd
```

Para navegar entre diretórios, usa-se o comando `cd`. Quando utilizamos um caminho absoluto, começamos a partir da raiz:

```bash
cd /home/usuario
```

Já um caminho relativo depende do diretório atual:

```bash
cd documentos
```

Essa diferença é essencial, pois define como o sistema localiza arquivos.

A manipulação de arquivos e diretórios é feita por comandos simples. Para listar arquivos:

```bash
ls
```

ou com mais detalhes:

```bash
ls -la
```

Para criar diretórios:

```bash
mkdir pasta
```

E arquivos:

```bash
touch arquivo.txt
```

Para copiar arquivos:

```bash
cp arquivo.txt copia.txt
```

Para mover ou renomear:

```bash
mv arquivo.txt novo_nome.txt
```

Para remover:

```bash
rm arquivo.txt
```

ou diretórios:

```bash
rm -r pasta
```

Cada arquivo no Linux possui permissões que controlam o acesso. Essas permissões definem quem pode ler, escrever ou executar um arquivo. Elas são divididas entre três categorias: dono (usuário), grupo e outros.

Ao usar:

```bash
ls -l
```

podemos ver algo como:

```
-rwxr-xr--
```

Isso indica as permissões do arquivo. Por exemplo, o dono pode ler, escrever e executar, enquanto outros usuários têm permissões mais limitadas. Esse sistema garante segurança e controle dentro do ambiente multiusuário do Linux.

---

## Iniciação do Sistema

Além da organização de arquivos, é importante entender como o sistema inicia, pois isso influencia diretamente o funcionamento do Linux.

Quando o computador é ligado, o primeiro software a ser executado não é o Linux, mas sim o firmware da máquina, que pode ser a **BIOS** ou a **UEFI**.

A **BIOS** (Basic Input/Output System) é um sistema mais antigo, responsável por realizar testes iniciais no hardware **(POST)**, verificando memória, disco e dispositivos. Após isso, ela procura um dispositivo de boot e carrega o sistema operacional.

A **UEFI* é a evolução da BIOS. Ela é mais moderna, suporta discos maiores (GPT), possui interface gráfica e recursos de segurança, como o Secure Boot.

Depois dessa etapa, entra em ação o **bootloader**, geralmente o GRUB. Ele permite escolher o sistema operacional e carrega o kernel do Linux.

Em seguida, o kernel assume o controle do sistema, inicializa o hardware, monta o sistema de arquivos raiz `/` e inicia os processos necessários para o funcionamento do sistema.

Na prática, isso significa que toda a estrutura de arquivos que você usa no dia a dia só existe porque foi corretamente carregada durante o processo de inicialização.

Por exemplo, ao acessar:

```bash
cd /home/usuario
```

você está utilizando um sistema de arquivos que foi montado durante o boot. Isso conecta diretamente o funcionamento do hardware com a organização lógica dos arquivos no Linux.