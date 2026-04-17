# 🔹 Capítulo 14 – Network Operations

## 🔹 Tópicos
- Endereçamento IP (IPv4 e IPv6)
- Resolução de Nomes (DNS)
- Ferramentas de Rede e Diagnóstico (ifconfig, ip, ping, route, traceroute)
- Navegadores Gráficos e de Texto (Firefox, Lynx, Konqueror, etc.)
- Downloads Web (wget e curl)
- Transferência de Arquivos (FTP e SFTP)
- SSH e Execução de Comandos Remotos

---

## 🔹 Subtópicos

### Redes e Endereçamento IP
O endereço IP (Internet Protocol) é um endereço lógico único atribuído a um dispositivo na rede. Todo endereço IP contém um campo de rede (network) e um campo de host.
- **IPv4 vs IPv6:** O IPv4 utiliza endereços de 32 bits, enquanto o IPv6 utiliza endereços de 128 bits.
- **Classes de Rede:** Existem cinco classes de endereços de rede disponíveis: A, B, C, D e E.
- **DNS (Domain Name System):** É o sistema utilizado para converter domínios da Internet e nomes de hosts em endereços IP compreensíveis pelas máquinas.



### Ferramentas de Rede e Diagnóstico
O Linux oferece ferramentas para exibir configurações, gerenciar rotas e depurar problemas de conectividade:
- **ifconfig e ip:** O programa ifconfig é usado para exibir as interfaces de rede ativas. Comandos modernos como "ip addr show" (para IPs) e "ip route show" (para roteamento) são essenciais.
- **ping:** Utilizado primariamente para verificar se um host remoto está online e respondendo. (Questão 14.1)
- **route:** Um utilitário em linha de comando usado para visualizar ou gerenciar as rotas de IP.
- **traceroute:** (Conteúdo Adicional) Utilizado para monitorar o caminho que um pacote percorre através da rede até o destino.

(abrir bash)
ping google.com
ip addr show
ip route show
(fechar bash)

### Navegadores e Transferência de Arquivos
O Linux suporta diversos navegadores para diferentes necessidades:
- **Navegadores Gráficos:** Mozilla Firefox, Google Chrome, Chromium, Epiphany e **Konqueror**. (Questão 14.2)
- **Navegadores de Texto:** Lynx, Links e w3m. Excelentes para ambientes sem interface gráfica.
- **Downloads Web:** Utilitários de linha de comando podem baixar conteúdo diretamente da Internet. O comando **wget** é usado para baixar páginas ou arquivos completos, e o utilitário **curl** é usado para obter informações e transferir dados a partir de URLs. (Questão 14.3)

(abrir bash)
wget https://example.com/file.zip
curl https://example.com
(fechar bash)

### Protocolos de Transferência e Segurança
- **FTP (File Transfer Protocol):** Utilizado para transferir arquivos pela rede. Clientes comuns incluem ftp, sftp, ncftp e yafc.
- **Aviso sobre FTP:** O FTP comum já não é considerado dentro dos padrões modernos pois possui mais de 40 anos de bagagem histórica e transmite senhas em texto puro (sem criptografia), podendo ser facilmente interceptadas. (Questão 14.4)

### SSH (Secure Shell) e Execução Remota
O **ssh** é usado para acessar sistemas remotos com total criptografia. Diferente de protocolos antigos, o SSH permite executar comandos diretamente no destino ou abrir sessões interativas usando múltiplas sintaxes válidas, como a flag `-l` (login) ou o formato `usuario@host`. (Questão 14.5)

(abrir bash)
# Sintaxe usando a flag -l:
ssh -l haskell eddie.com

# Sintaxe direta usuario@host para executar um comando remoto:
ssh root@eddie.com yum -y update

# Combinando flag -l com execução de comando:
ssh -l haskell eddie.com whoami
(fechar bash)

---

# 🔹 Conteúdo

Neste capítulo, aprendi que cada dispositivo conectado a uma rede recebe um endereço lógico único chamado IP, sendo o IPv4 de 32 bits e o IPv6 de 128 bits. Compreendi que esses endereços são divididos em campos de rede e host, distribuídos em cinco classes (A a E), e que o DNS é o responsável por traduzir nomes de domínios legíveis para esses IPs numéricos.

Na prática de diagnóstico, aprendi a verificar se um host remoto está online usando o comando ping e a monitorar o caminho dos dados com o traceroute. Entendi como listar minhas interfaces de rede ativas usando ifconfig e os comandos modernos ip addr show e ip route show para gerenciar tabelas de roteamento.

Explorei as opções de navegação na web, diferenciando navegadores gráficos como Firefox e Konqueror de navegadores de modo texto como Lynx e Links. Também dominei ferramentas como wget e curl para realizar downloads e consultar URLs diretamente pelo terminal. Por fim, compreendi os riscos de segurança do antigo protocolo FTP, que transmite senhas sem criptografia, e como o SSH resolve esse problema, permitindo acesso remoto seguro através de sintaxes flexíveis como o uso do "usuario@host" ou da flag "-l", garantindo a execução de comandos em outras máquinas com total proteção.

---

# Comandos do Capítulo

| Comando | Descrição |
|--------|-----------|
| ifconfig | Exibe as interfaces de rede ativas no sistema. |
| ip addr show | Exibe endereços IP e informações das interfaces. |
| ip route show | Exibe informações da tabela de roteamento. |
| ping | Verifica se um host remoto está online e respondendo (Questão 14.1). |
| route | Utilitário para visualizar ou gerenciar rotas de IP. |
| traceroute | Monitora o caminho dos pacotes pela rede. |
| wget | Baixa arquivos ou páginas da web (Questão 14.3). |
| curl | Obtém informações de URLs e transfere dados (Questão 14.3). |
| ftp / sftp | Clientes para transferência de arquivos (sftp é seguro). |
| ssh | Acesso remoto seguro e execução de comandos (Questão 14.5). |
| lynx / links | Navegadores web que funcionam em modo texto. |

---

# Explicação detalhada dos Comandos Básicos do Linux

## Diagnóstico de Rede (ping e traceroute)
O comando ping envia pacotes de teste para um destino e aguarda a resposta para confirmar que a conexão está ativa. Já o traceroute mapeia cada salto (roteador) que o pacote dá até chegar ao seu destino final, ajudando a identificar onde uma conexão está falhando.

## Configuração de IP (ifconfig e ip)
O ifconfig é a ferramenta tradicional, enquanto a suíte ip é a sucessora moderna. Elas permitem que o administrador veja o endereço IP atribuído a cada placa de rede e verifique o estado do hardware de rede.

## Navegadores (Gráficos vs Texto)
O Linux permite navegar de forma gráfica (Firefox, Konqueror) ou via terminal (Lynx). O Konqueror é notável por ser um navegador e gerenciador de arquivos integrado, enquanto o Lynx é a escolha principal para servidores sem interface de vídeo.

## Transferência Web (wget e curl)
O wget é excelente para baixar arquivos grandes ou recursivos. O curl é mais focado na comunicação direta com o servidor, permitindo ver cabeçalhos de resposta e interagir com APIs de forma rápida.

## Acesso Remoto (SSH)
O SSH cria um túnel criptografado entre sua máquina e o servidor. Ele suporta diferentes formas de autenticação e execução; você pode usar `ssh usuario@servidor` ou `ssh -l usuario servidor`. Diferente do FTP, que é inseguro por expor senhas em texto puro, o SSH protege toda a sessão.

---

## 🔹 Recursos úteis
- https://linuxcommand.org
- https://kernel.org
- https://gnu.org