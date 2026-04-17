# Capítulo 2 — Filosofia e Conceitos do Linux

## O que é Linux?

>O **Linux** é um sistema operacional de código aberto inspirado no **Unix**. Ele não é apenas um programa único, mas sim um conjunto de componentes que trabalham juntos. O principal deles é o **kernel**, que funciona como o núcleo do sistema, sendo responsável por controlar o hardware, gerenciar memória, processos e dispositivos.

Quando falamos em “usar Linux”, na prática estamos usando uma **distribuição Linux**, que inclui:

- Kernel  
- Programas básicos  
- Bibliotecas  
- Aplicativos  

Ou seja, o Linux completo é a soma de vários projetos diferentes que trabalham juntos.

>Um ponto muito importante é que o Linux é  **open source (código aberto)**. Isso significa que qualquer pessoa pode estudar, modificar e distribuir o sistema. Essa característica permite evolução constante, maior segurança e grande diversidade de versões.

---

## Filosofia do Linux

O Linux segue princípios herdados do Unix, que influenciam diretamente sua forma de funcionamento:

- Fazer uma coisa e fazer bem feita  
- Permitir combinação de ferramentas  
- Dar controle ao usuário  
- Trabalhar com simplicidade e eficiência  

> **“Tudo no Linux é um arquivo”**

Isso significa que:

- Arquivos comuns → textos, imagens  
- Dispositivos → HD, teclado (`/dev`)  
- Processos → informações em `/proc`  

### Exemplo prático

```bash
cat /proc/cpuinfo
```

Esse comando mostra informações do processador como se fosse um arquivo comum.

---

## Estrutura do Sistema

O sistema Linux é organizado em forma de árvore, começando pelo diretório raiz:

```
/
```

A partir dele, tudo é organizado.

### Exemplo de caminho

```
/home/usuario/documento.txt
```

### Tipos de caminhos

- **Absoluto** → começa com `/`  
- **Relativo** → baseado no diretório atual  

### Exemplo

```bash
cd /home
cd usuario
```

---

## Famílias e Distribuições Linux

O Linux possui várias distribuições organizadas em famílias. Cada família compartilha características, ferramentas e filosofia.

### Principais famílias:

- Red Hat  
- SUSE  
- Debian  

---

## Família Red Hat

A família Red Hat é muito utilizada em ambientes corporativos.

### Sistema principal

- **Red Hat Enterprise Linux (RHEL)**  

### Outras distribuições

- Fedora  
- CentOS / CentOS Stream  
- Oracle Linux  

O Fedora é mais moderno e recebe novidades primeiro. Ele funciona como um ambiente de testes para tecnologias que depois serão utilizadas no RHEL.

---

## Família SUSE

A família SUSE também possui foco empresarial.

### Principais sistemas

- **SUSE Linux Enterprise (SLES)**
- **openSUSE**

O openSUSE é a versão gratuita e muito utilizada para aprendizado.

Um diferencial importante é o **YaST (Yet another Setup Tool)**, uma ferramenta que facilita a configuração do sistema.

### Exemplo

É possível configurar rede, usuários e serviços utilizando uma interface gráfica, sem precisar digitar comandos no terminal.

---

## Família Debian

A família Debian é uma das mais importantes e populares no mundo Linux.

### Principais características

- Alta estabilidade  
- Comunidade forte  
- Grande quantidade de softwares disponíveis  

### Distribuições baseadas

- Debian  
- Ubuntu  
- Linux Mint  

O Debian é extremamente estável e amplamente utilizado em servidores.

O Ubuntu é mais fácil de usar e muito popular em desktops, sendo uma das principais portas de entrada para novos usuários no Linux.
