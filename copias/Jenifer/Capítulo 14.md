# Capítulo 14 — Redes no Linux (Explicação Completa)

No Linux, a comunicação em rede é baseada no conceito de **endereçamento IP**, que funciona como um “identificador único” para cada dispositivo conectado. Assim como uma casa precisa de um endereço para receber correspondências, um computador precisa de um IP para enviar e receber dados.

O sistema trabalha principalmente com dois tipos de IP: o **IPv4**, que utiliza 32 bits (exemplo: `192.168.0.1`), e o **IPv6**, mais moderno, que utiliza 128 bits e permite uma quantidade muito maior de dispositivos conectados. Mesmo com o avanço do IPv6, o IPv4 ainda é amplamente utilizado.

Cada endereço IP possui duas partes importantes: a **rede** (que identifica o conjunto de dispositivos) e o **host** (que identifica o dispositivo dentro dessa rede). Isso permite organizar redes grandes de forma eficiente.

Para facilitar o uso, não precisamos decorar IPs. Existe o **DNS (Domain Name System)**, que traduz nomes como `google.com` para um endereço IP real. Sem o DNS, a navegação na internet seria muito mais difícil.

No Linux, é possível visualizar e gerenciar configurações de rede usando comandos. Por exemplo:

- `ip addr show` → mostra os endereços IP da máquina
- `ip route show` → mostra as rotas de rede

Um exemplo prático:

```bash
ip addr show
```

Esse comando exibe todas as interfaces de rede (como Wi-Fi ou cabo) e seus respectivos IPs.

Para testar se um dispositivo está acessível na rede, usamos o comando:

```bash
ping google.com
```

Se houver resposta, significa que o host está ativo e a comunicação está funcionando.

Outro comando importante é o `traceroute`, que mostra o caminho que os dados percorrem até chegar ao destino, passando por vários roteadores.

Além disso, o Linux possui ferramentas mais avançadas para análise de rede, como:

- `netstat` → mostra conexões ativas
- `nmap` → faz varredura de rede
- `tcpdump` → analisa pacotes de dados

Para acessar conteúdos da internet, o Linux oferece navegadores gráficos e também opções em modo texto, como:

```bash
lynx google.com
```

Para download de arquivos, existem ferramentas muito utilizadas:

```bash
wget https://site.com/arquivo.zip
```

ou

```bash
curl -O https://site.com/arquivo.zip
```

Essas ferramentas são muito usadas em servidores e automações.

Na transferência de arquivos, o protocolo FTP foi muito usado no passado, mas não é seguro. Hoje, utilizam-se alternativas como:

- **SFTP** (FTP seguro)
- **SCP** (cópia segura via SSH)

Exemplo:

```bash
scp arquivo.txt usuario@servidor:/home/usuario
```

O **SSH (Secure Shell)** é um dos recursos mais importantes do Linux, pois permite acessar outro computador remotamente com segurança:

```bash
ssh usuario@servidor
```

Com isso, é possível administrar servidores inteiros à distância, executar comandos e transferir arquivos com segurança.

Em resumo, o Linux oferece um conjunto extremamente poderoso de ferramentas de rede, permitindo desde tarefas simples, como testar conexão, até atividades avançadas, como análise de tráfego e administração remota de sistemas.