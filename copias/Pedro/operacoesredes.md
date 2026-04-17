# Operações de Redes no Linux

## 1. Conceitos Básicos de Redes

Uma rede de computadores permite a troca de dados entre dispositivos através de protocolos padronizados (como o TCP/IP).

### Tipos de Redes
* **LAN (Local Area Network):** Redes locais, como a de sua casa ou escritório.
* **WAN (Wide Area Network):** Redes de longa distância, sendo a Internet o maior exemplo.
* **WLAN:** Redes locais sem fio (Wi-Fi).

### Resolução de Questões (Troubleshooting)
O diagnóstico de rede no Linux geralmente segue uma ordem lógica:
1. **Conectividade Física/Link:** A interface está ativa?
2. **Endereçamento IP:** O dispositivo tem um IP na sub-rede correta?
3. **Roteamento:** O dispositivo alcança o Gateway (roteador)?
4. **DNS:** O sistema consegue traduzir nomes (google.com) em IPs?

---

## 2. Configuração e Utilitários de Rede

No Linux moderno, o comando `ip` substituiu o antigo `ifconfig`, mas ambos ainda são encontrados.

### Comandos de Inspeção e Configuração
* **`ip addr`:** Exibe os endereços IP e detalhes das interfaces.
* **`ip link set eth0 up`:** Ativa uma interface de rede específica.
* **`ifconfig`:** Utilitário clássico para visualizar IPs (requer pacote `net-tools`).

### Teste e Roteamento
* **`ping <ip_ou_host>`:** Testa a conectividade básica e a latência entre dois pontos.
* **`route -n` ou `ip route`:** Exibe a tabela de roteamento do sistema (identifica o Gateway padrão).
* **`traceroute <host>`:** Mostra o caminho (saltos pelos roteadores) que um pacote percorre até o destino.
* **`nslookup` / `dig <host>`:** Utilizados para testar a resolução de nomes (DNS).

---

## 3. Navegação Web (Gráfica e Texto)

O Linux oferece flexibilidade para acessar a web mesmo em servidores sem interface gráfica.

### Navegadores Gráficos (GUI)
* **Firefox:** O padrão na maioria das distribuições, altamente seguro.
* **Chrome / Chromium:** Baseado no motor Blink, popular pela performance.
* **Epiphany (GNOME Web):** Navegador leve e integrado ao ambiente GNOME.

### Navegadores de Terminal (CLI)
Úteis para servidores ou conexões lentas:
* **`lynx`:** Um dos mais antigos, puramente baseado em texto.
* **`w3m`:** Suporta tabelas e até renderização básica de imagens em terminais compatíveis.

---

## 4. Transferência de Arquivos

Existem diversas formas de mover dados entre clientes e servidores, dependendo do protocolo e da interface.

### Ferramentas de Linha de Comando (CLI)
* **`scp` (Secure Copy):** Copia arquivos via SSH de forma segura.
    * *Ex:* `scp arquivo.txt usuario@ip:/home/usuario/`
* **`sftp`:** Protocolo de transferência de arquivos interativo sobre SSH.
* **`ftp`:** Protocolo clássico (não criptografado) para transferência de arquivos.
* **`curl`:** Ferramenta poderosa para transferir dados de ou para um servidor (suporta HTTP, FTP, etc).
    * *Ex:* `curl -O http://site.com/arquivo.zip`
* **`wget`:** Ideal para downloads recursivos e recuperáveis.
    * *Ex:* `wget -c http://site.com/arquivo.iso`

### Ferramentas Gráficas (GUI)
* **FileZilla:** Cliente FTP/SFTP completo com interface de arrastar e soltar.
* **Nautilus / Dolphin / Thunar:** Os gerenciadores de arquivos nativos permitem conectar a servidores via `sftp://` ou `ftp://` diretamente na barra de endereços.

---
> **Dica:** Para verificar quais portas estão abertas e ouvindo conexões no seu sistema, utilize o comando `ss -tuln` ou o clássico `netstat -plnt`.