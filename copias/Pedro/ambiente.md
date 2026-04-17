# Administração e Configuração do Ambiente Linux

## 1. Gestão de Usuários e Grupos

O Linux é um sistema multiusuário. O controle de acesso é baseado em contas de usuário e grupos.

### Usuários
* **Criar usuário:** `sudo adduser nome_usuario`
* **Remover usuário:** `sudo deluser nome_usuario`
* **Alterar senha:** `passwd nome_usuario`

### Grupos
* **Criar grupo:** `sudo addgroup nome_grupo`
* **Adicionar usuário a um grupo:** `sudo usermod -aG nome_grupo nome_usuario`
* **Ver grupos do usuário atual:** `groups`

---

## 2. Permissões e Propriedade de Arquivos

A segurança do sistema depende de quem pode ler, escrever ou executar arquivos.

### Propriedade (Ownership)
* **Alterar dono:** `sudo chown usuario arquivo`
* **Alterar grupo:** `sudo chgrp grupo arquivo`
* **Alterar ambos:** `sudo chown usuario:grupo arquivo`

### Permissões
As permissões são divididas em **Dono (u)**, **Grupo (g)** e **Outros (o)**.
* **chmod:** Altera as permissões.
    * *Modo Simbólico:* `chmod u+x arquivo` (adiciona execução para o dono).
    * *Modo Numérico:* `chmod 755 arquivo` (rwx para dono, r-x para grupo e outros).

---

## 3. Variáveis de Ambiente

Variáveis de ambiente armazenam informações usadas por processos e pelo shell.

* **Listar todas as variáveis:** `env` ou `printenv`
* **Definir variável temporária:** `NOME="Valor"`
* **Tornar variável disponível para sub-processos:** `export NOME="Valor"`
* **Variáveis importantes:**
    * `$PATH`: Define os diretórios onde o sistema busca executáveis.
    * `$USER`: Nome do usuário atual.
    * `$HOME`: Caminho para o diretório pessoal.

---

## 4. Atalhos e Histórico do Shell

Aumentar a velocidade de operação no terminal.

### Histórico de Comandos
* **`history`:** Exibe a lista de comandos executados anteriormente.
* **`!!`:** Executa o último comando novamente.
* **`!n`:** Executa o comando de número `n` do histórico.
* **`Ctrl + R`:** Pesquisa reversa no histórico (digite para buscar).

### Atalhos de Teclado Essenciais
* **`Tab`:** Autocompleta nomes de arquivos, caminhos e comandos.
* **`Ctrl + C`:** Interrompe/Mata o processo atual.
* **`Ctrl + L`:** Limpa a tela do terminal.
* **`Ctrl + A` / `Ctrl + E`:** Move o cursor para o início / fim da linha.

---

## 5. Apelidos (Aliases)

Os aliases permitem criar "atalhos" para comandos longos ou complexos.

* **Definir apelido temporário:** `alias ll='ls -lah'`
* **Remover apelido:** `unalias ll`
* **Tornar permanente:** Adicione o comando `alias` ao seu arquivo `~/.bashrc` ou `~/.zshrc`.

Exemplo útil:
```bash
alias update='sudo apt update && sudo apt upgrade'