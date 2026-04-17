# Capítulo 12 — Ambiente do Usuário

O Linux é um sistema **multiusuário**, o que significa que várias pessoas podem usar o mesmo sistema ao mesmo tempo, cada uma com sua própria conta, arquivos e permissões. Isso é muito importante principalmente em servidores, onde vários usuários acessam o mesmo sistema simultaneamente.

Para saber quem está conectado no sistema naquele momento, pode-se usar:

```bash
who
```

Já para saber qual é o usuário atual:

```bash
whoami
```

Cada usuário possui um identificador único (UID) e pertence a um ou mais grupos, que ajudam a organizar permissões e acessos.

---

### Usuário root e sudo

No Linux, existe um usuário especial chamado **root**, que tem acesso total ao sistema. Ele pode fazer qualquer alteração, instalar programas, modificar arquivos críticos e até apagar o sistema inteiro.

Por isso, usar o root diretamente não é recomendado. Em vez disso, utiliza-se o comando:

```bash
sudo comando
```

O `sudo` permite executar apenas um comando com privilégios administrativos, usando a senha do próprio usuário. Isso é muito mais seguro.

Exemplo:

```bash
sudo apt update
```

---

### Arquivos de inicialização do shell

Quando um usuário faz login ou abre o terminal, o sistema carrega automaticamente alguns arquivos que configuram o ambiente. Esses arquivos são chamados de **arquivos de inicialização**.

O principal arquivo global é:

```bash
/etc/profile
```

Ele define configurações para todos os usuários.

Já no diretório pessoal do usuário (`~`), existem arquivos como:

- `.bashrc`
- `.profile`
- `.bash_profile`

Esses arquivos permitem personalizar o ambiente do terminal.

---

### Personalização do ambiente

Com os arquivos de inicialização, você pode:

- Alterar o prompt do terminal
- Criar atalhos (aliases)
- Definir variáveis de ambiente
- Configurar programas padrão

Por exemplo, criar um alias:

```bash
alias ll='ls -l'
```

Agora, ao digitar `ll`, o sistema executa `ls -l`.

Para tornar permanente, basta adicionar no arquivo:

```bash
~/.bashrc
```

---

### Variáveis de ambiente

As **variáveis de ambiente** são valores armazenados que influenciam o funcionamento do sistema e dos programas.

Exemplo:

```bash
echo $HOME
```

Mostra o diretório do usuário.

Outra variável importante:

```bash
echo $PATH
```

Ela define onde o sistema procura programas executáveis.

Você pode criar uma variável:

```bash
VAR=teste
```

E exportar:

```bash
export VAR
```

---

### Histórico de comandos

O Linux salva os comandos que você digitou, permitindo reutilizá-los.

Para ver:

```bash
history
```

Você pode repetir um comando anterior ou buscá-lo rapidamente, o que economiza muito tempo.

---

### Atalhos de teclado

O terminal possui vários atalhos úteis, por exemplo:

- `Ctrl + C` → interrompe um comando
- `Ctrl + L` → limpa a tela
- `Tab` → autocompleta comandos
- `↑ ↓` → navega no histórico

Esses atalhos tornam o uso do terminal muito mais rápido.

---

### Permissões de arquivos

Cada arquivo no Linux possui permissões que controlam quem pode acessá-lo.

Existem três tipos:

- leitura (r)
- escrita (w)
- execução (x)

E três níveis:

- dono
- grupo
- outros

Para alterar permissões:

```bash
chmod 755 arquivo
```

Ou de forma simbólica:

```bash
chmod u+x arquivo
```

---

### Propriedade de arquivos

Cada arquivo pertence a um usuário e a um grupo.

Para alterar o dono:

```bash
chown usuario arquivo
```

Para alterar o grupo:

```bash
chgrp grupo arquivo
```

Exemplo:

```bash
sudo chown root arquivo.txt
```