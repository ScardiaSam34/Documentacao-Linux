# Princípios de Segurança no Linux

A segurança em sistemas Linux é baseada em boas práticas, controle de acesso rigoroso e uso consciente de ferramentas administrativas. Este documento apresenta conceitos fundamentais para tornar um sistema Linux mais seguro.

---

## 1. Boas práticas e ferramentas de segurança

Para manter um sistema Linux seguro, é essencial adotar práticas consistentes:

### 1.1 Atualizações regulares

Manter o sistema atualizado corrige vulnerabilidades conhecidas:

```bash
sudo apt update && sudo apt upgrade
```

ou

```bash
sudo dnf update
```

### 1.2 Uso de firewall

Ferramentas como `ufw` (Uncomplicated Firewall) ajudam a controlar o tráfego:

```bash
sudo ufw enable
sudo ufw allow ssh
```

### 1.3 Monitoramento e logs

Logs do sistema ajudam a identificar atividades suspeitas:

```bash
sudo journalctl
```

### 1.4 Controle de acesso

* Utilize permissões de arquivos corretamente (`chmod`, `chown`)
* Evite acesso desnecessário a arquivos sensíveis

---

## 2. Conta root: poderes e perigos

A conta **root** possui controle total sobre o sistema:

### 2.1 Poderes

* Instalar/remover softwares
* Alterar configurações críticas
* Gerenciar usuários e permissões

### 2.2 Perigos

* Execução acidental de comandos destrutivos
* Maior risco em caso de invasão
* Falta de rastreabilidade (sem distinção de usuários)

### 2.3 Boas práticas

* Evitar login direto como root
* Utilizar contas comuns para tarefas diárias

---

## 3. Uso do comando sudo

O comando `sudo` permite executar tarefas administrativas com segurança:

```bash
sudo comando
```

### 3.1 Vantagens

* Registra ações realizadas
* Limita privilégios temporariamente
* Permite controle granular de permissões

### 3.2 Configuração

Editar o arquivo de permissões com:

```bash
sudo visudo
```

### 3.3 Boas práticas

* Conceder privilégios apenas a usuários necessários
* Evitar uso contínuo de sudo sem necessidade

---

## 4. Isolamento de processos e acesso ao hardware

### 4.1 Isolamento de processos

Cada processo no Linux roda em seu próprio espaço de memória, o que evita:

* Interferência entre programas
* Acesso não autorizado a dados de outros processos

Ferramentas como **containers** e namespaces reforçam esse isolamento.

### 4.2 Acesso ao hardware

O acesso direto ao hardware é restrito:

* Apenas root ou usuários autorizados podem acessar dispositivos críticos
* Dispositivos são representados em `/dev`

Controle de permissões:

```bash
ls -l /dev
```

---

## 5. Gerenciamento de senhas

### 5.1 Definindo senha

```bash
passwd
```

### 5.2 Alterando senha de outro usuário (root)

```bash
sudo passwd usuario
```

### 5.3 Boas práticas de senha

* Utilizar senhas fortes (mínimo 8 caracteres, incluindo números e símbolos)
* Evitar reutilização
* Alterar senhas periodicamente

### 5.4 Políticas de senha

Configurações podem ser feitas em:

```bash
/etc/login.defs
```

---

## 6. Proteção do processo de inicialização e hardware

### 6.1 Protegendo o bootloader

O bootloader (como GRUB) pode ser protegido com senha para evitar alterações:

```bash
sudo grub-mkpasswd-pbkdf2
```

Depois, configurar no arquivo do GRUB.

### 6.2 BIOS/UEFI

* Definir senha de acesso
* Desativar boot por dispositivos externos

### 6.3 Criptografia de disco

Protege dados em caso de acesso físico:

* Utilizar LUKS (Linux Unified Key Setup)

### 6.4 Controle físico

* Restringir acesso físico ao equipamento
* Monitorar portas USB e dispositivos externos

---

## Conclusão

A segurança no Linux depende da combinação de boas práticas, ferramentas adequadas e uso consciente de privilégios. O uso correto do `sudo`, controle de acesso, proteção do boot e gerenciamento de senhas são fundamentais para manter um sistema protegido contra ameaças.

---
