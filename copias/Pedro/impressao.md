# Impressão no Linux

A impressão em sistemas Linux é um processo flexível e poderoso, suportando diversos tipos de impressoras e formatos de arquivos. Este documento apresenta como configurar uma impressora, imprimir documentos e manipular arquivos PostScript e PDF utilizando utilidades da linha de comando.

---

## 1. Configuração de Impressora no Linux

A maioria das distribuições Linux utiliza o sistema **CUPS (Common Unix Printing System)** para gerenciar impressões.

### 1.1 Instalação do CUPS

Em distribuições baseadas em Debian/Ubuntu:

```bash
sudo apt update
sudo apt install cups
```

Em distribuições baseadas em Fedora:

```bash
sudo dnf install cups
```

### 1.2 Inicialização do serviço

```bash
sudo systemctl start cups
sudo systemctl enable cups
```

### 1.3 Acesso à interface web

Abra o navegador e acesse:

```
http://localhost:631
```

### 1.4 Adicionando uma impressora

1. Clique em **Administration**
2. Selecione **Add Printer**
3. Escolha a impressora (USB, rede, etc.)
4. Instale o driver apropriado

---

## 2. Impressão de Documentos

### 2.1 Comando básico (`lp`)

```bash
lp arquivo.txt
```

### 2.2 Especificando impressora

```bash
lp -d nome_da_impressora arquivo.pdf
```

### 2.3 Número de cópias

```bash
lp -n 3 arquivo.pdf
```

### 2.4 Verificando fila de impressão

```bash
lpq
```

### 2.5 Cancelando impressão

```bash
cancel ID_DO_TRABALHO
```

---

## 3. Manipulação de Arquivos PostScript e PDF

O Linux oferece diversas ferramentas para manipulação desses formatos diretamente pelo terminal.

### 3.1 Arquivos PostScript (PS)

#### Visualizar arquivo

```bash
gv arquivo.ps
```

#### Converter PS para PDF

```bash
ps2pdf arquivo.ps arquivo.pdf
```

#### Gerar PS a partir de texto

```bash
enscript arquivo.txt -o arquivo.ps
```

---

### 3.2 Arquivos PDF

#### Visualizar PDF

```bash
evince arquivo.pdf
```

#### Converter PDF para PS

```bash
pdf2ps arquivo.pdf arquivo.ps
```

#### Extrair texto de PDF

```bash
pdftotext arquivo.pdf
```

#### Unir PDFs

```bash
pdfunite arquivo1.pdf arquivo2.pdf saida.pdf
```

#### Dividir PDF

```bash
pdfseparate arquivo.pdf pagina-%d.pdf
```

---

### 3.3 Impressão de arquivos PDF e PS

```bash
lp arquivo.pdf
```

```bash
lp arquivo.ps
```

---

## Conclusão

O Linux fornece um ambiente robusto para impressão, com ferramentas que permitem desde configurações simples até automações avançadas. O uso do CUPS simplifica a administração de impressoras, enquanto utilitários de linha de comando oferecem grande flexibilidade na manipulação de documentos.

---
