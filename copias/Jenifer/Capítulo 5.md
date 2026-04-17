# Capítulo 5 — Configurações do Sistema

No Linux, grande parte das configurações do sistema pode ser feita de forma simples através do painel de **Configurações do Sistema**, presente no ambiente gráfico.

Esse painel funciona como um **centro de controle**, permitindo ajustar desde opções básicas até configurações mais avançadas, sem a necessidade de utilizar o terminal.

---
## Data e Hora

Uma das configurações mais importantes é a de **data e hora**.

Internamente, o Linux utiliza o padrão **UTC (Tempo Universal Coordenado)**, garantindo consistência entre sistemas, especialmente em servidores e ambientes de rede.

Para o usuário:

- O sistema ajusta automaticamente o horário conforme o fuso configurado  
- É possível ativar sincronização automática via internet  

Essa sincronização é feita através do:

- **NTP (Network Time Protocol)** → mantém o relógio sempre correto  

---

## Monitores

O sistema também permite configurar facilmente os **dispositivos de vídeo**.

Principais opções:

- Alterar resolução da tela  
- Ajustar orientação (horizontal/vertical)  
- Configurar múltiplos monitores  

Esse recurso é muito utilizado em ambientes profissionais, onde o uso de duas ou mais telas aumenta a produtividade.

---

## Rede

O Linux possui um sistema completo de gerenciamento de rede através do **Gerenciador de Rede**.

Com ele, é possível:

- Visualizar redes Wi-Fi disponíveis  
- Conectar-se a redes  
- Salvar senhas  
- Configurar redes móveis  
- Criar conexões seguras (VPN)  

Tudo isso pode ser feito de forma gráfica, facilitando o uso mesmo para iniciantes.

---

## Gerenciamento de Pacotes

Outro ponto essencial é o **gerenciamento de pacotes**, que define como programas são:

- Instalados  
- Atualizados  
- Removidos  

Diferente de outros sistemas, no Linux os softwares são obtidos de **repositórios oficiais**, garantindo mais segurança e organização.

---

### Sistemas principais

Existem dois modelos mais comuns:

#### Distribuições baseadas em Debian (Ubuntu, etc.)

Utilizam:

- **dpkg** → gerenciador base  
- **apt** → ferramenta que automatiza o processo  

Exemplo de instalação:

```bash
sudo apt install firefox
```

Esse comando instala o programa e todas as dependências necessárias automaticamente.

---

#### Distribuições baseadas em Red Hat

Utilizam sistemas baseados em **RPM**, com ferramentas como:

- `dnf`
- `yum`

Essas ferramentas possuem funções semelhantes ao `apt`.

