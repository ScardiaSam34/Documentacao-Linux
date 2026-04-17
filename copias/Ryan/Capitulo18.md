# 🔹 Capítulo 18 – Local Security Principles

## 🔹 Tópicos
- Compreendendo a Segurança no Linux (Contas e Usuários)
- Quando Privilégios de Administrador (root) São Necessários?
- O Comando sudo, su e Auditoria de Logs
- Trabalhando com Senhas (Armazenamento, PAM e chage)
- Isolamento de Processos e Segurança de Hardware

---

## 🔹 Subtópicos

### Contas de Usuário e o Usuário "root"
A segurança no Linux é baseada em identidades e permissões. O sistema verifica a autenticidade e identidade através das credenciais fornecidas.
- **Usuários Regulares:** Têm controle sobre seu próprio diretório (/home), mas não alteram o sistema.
- **Contas de Sistema (System Accounts):** Usadas por serviços para rodar processos com permissões limitadas.
- **O Usuário root:** É a conta com autoridade suprema sobre todo o sistema.
- **Auditoria de Acesso:** O comando **last** é essencial para identificar logins recentes e verificar há quanto tempo uma conta de usuário permanece inativa.

### Quando Privilégios de "root" São Necessários?
- **Exigem root:** Reiniciar serviços, instalar/remover pacotes de software globalmente, modificar arquivos fora do /home (como no /etc) e gerenciar hardware.
- **NÃO exigem root:** Acessar arquivos que o usuário já tem permissão de leitura/escrita e acessar dispositivos de uso comum, como impressoras (dependendo da política local).

### O Comando sudo, su e Auditoria
Para realizar operações privilegiadas, usamos o **su** ou o **sudo**.
- **su (Substitute User):** Troca para outro usuário (geralmente root). Requer a senha do destino.
- **sudo (Superuser DO):** Executa comandos como root usando a senha do próprio usuário. Ele consulta o arquivo **/etc/sudoers** (editado via **visudo**) para validar se o usuário tem permissão.
- **Logging (Logs):** O sudo registra todas as tentativas (sucessos e falhas). 
  - Na família **Debian/Ubuntu**: **/var/log/auth.log**.
  - Em outras distribuições (Red Hat/CentOS): **/var/log/messages**.

### Trabalhando com Senhas (Armazenamento e Expiração)
- **Armazenamento:** As senhas modernas (shadow passwords) ficam no arquivo **/etc/shadow**, protegidas por criptografia **SHA-512** (um hash unidirecional que não pode ser descriptografado).
- **PAM (Pluggable Authentication Modules):** Mecanismo que verifica automaticamente se as senhas criadas pelo comando **passwd** são fortes o suficiente.
- **chage (Password Aging):** Utilitário que garante que as senhas, se descobertas, só sejam úteis por tempo limitado, forçando a expiração e troca periódica.

### Isolamento de Processos e Vulnerabilidades de Hardware
- **Process Isolation:** Um processo não pode acessar os recursos de outro, mesmo que rodem sob o mesmo usuário.
- **Segurança Física:** Se o hardware for acessível, a segurança pode ser comprometida por:
  - **Key logging:** Captura de tudo o que é digitado.
  - **Network sniffing:** Interceptação de tráfego de dados na rede.
  - **Remontagem de discos:** Modificação do conteúdo do disco via sistemas externos.
- **Boot Loader:** A configuração de uma senha no GRUB evita que invasores ganhem acesso root reiniciando a máquina em modo monousuário.
- **Keeping Current:** Manter o sistema atualizado é a defesa primária contra vulnerabilidades de software.

---

# 🔹 Conteúdo

Neste capítulo, explorei os pilares da segurança local, entendendo que o usuário **root** é o centro da autoridade no Linux. Aprendi que operações críticas, como gerenciar softwares e serviços, exigem esse poder, mas que para o uso diário, o ideal é operar como um usuário comum para evitar danos acidentais. Descobri ferramentas de auditoria como o comando **last**, que me permite ver quem logou no sistema e identificar contas inativas que podem representar um risco.

Dominei a diferença entre o **su** e o **sudo**. Vi que o sudo é muito mais robusto para administração moderna, pois utiliza o arquivo **/etc/sudoers** para controlar permissões e registra cada ação (ou falha) em logs de sistema, como o **/var/log/auth.log**. Aprendi também a importância de nunca editar esse arquivo de configuração diretamente, usando sempre o **visudo**.

No campo da criptografia, entendi que o Linux protege nossas senhas transformando-as em hashes **SHA-512** guardados no arquivo **/etc/shadow**. Compreendi como o **PAM** atua como um filtro de qualidade para senhas novas e como o comando **chage** é vital para implementar políticas de envelhecimento de senha, garantindo que as credenciais expirem periodicamente.

Por fim, entendi que a segurança é multicamadas. O sistema isola processos para que um programa não interfira no outro, mas nada disso adianta se houver vulnerabilidade física. Aprendi que o acesso direto ao hardware permite ataques como **key logging** e **network sniffing**, e que proteger o processo de boot com senhas e manter o sistema atualizado são passos inegociáveis para qualquer administrador que deseje manter a integridade do ambiente.

---

# Comandos e Operadores do Capítulo

| Comando / Arquivo | Descrição |
|--------|-----------|
| root | Conta de superusuário com autoridade total. |
| sudo | Executa comandos como root usando a própria senha (gera logs). |
| last | Exibe o histórico de logins e identifica usuários inativos. |
| chage | Gerencia o envelhecimento e expiração de senhas (Password Aging). |
| passwd | Utilitário para criar ou modificar senhas. |
| /etc/shadow | Onde as senhas criptografadas (hashes) são armazenadas de forma segura. |
| /var/log/auth.log | Log de autenticação (Debian) que registra sucessos e falhas de login/sudo. |
| visudo | Comando seguro para editar o arquivo de regras do sudo (/etc/sudoers). |
| PAM | Sistema que aplica regras de força e complexidade para as senhas. |
| SHA-512 | Algoritmo de hash padrão usado para proteger senhas no Linux. |

# Explicação Detalhada e Exemplos

## Auditoria e Expiração de Senha
Como administrador, você pode verificar quem está usando o sistema e forçar políticas de segurança.

(abrir bash)
# Ver quem logou no sistema ultimamente:
last

# Configurar a senha do usuário 'aluno' para expirar em 30 dias:
sudo chage -M 30 aluno
(fechar bash)

## Verificando Tentativas de Sudo
O log de segurança mostra exatamente o que foi tentado, mesmo que o usuário tenha errado a senha.

(abrir bash)
# Verificando os logs de autenticação (Debian/Ubuntu):
sudo tail -n 20 /var/log/auth.log
(fechar bash)

## Proteção de Arquivos Críticos
O acesso a arquivos como o shadow é restrito para proteger os hashes das senhas.

(abrir bash)
# Tentando ler o arquivo de senhas sem sudo (vai falhar):
cat /etc/shadow

# Lendo com privilégios (o hash SHA-512 será visível):
sudo cat /etc/shadow
(fechar bash)

---

## 🔹 Recursos úteis
- https://linuxcommand.org 
- https://kernel.org 
- https://gnu.org