# Capítulo 13 — Manipulação de Texto

Uma das maiores forças do Linux é a capacidade de manipular texto diretamente pela linha de comando. Muitas vezes, trabalhar no terminal é mais rápido e eficiente do que usar interface gráfica, principalmente quando se trata de processar grandes volumes de dados, logs ou arquivos de configuração.

O comando `cat` é um dos mais básicos e serve para visualizar o conteúdo de arquivos ou até combinar vários arquivos em um só. Por exemplo:

```bash
cat arquivo.txt
```

Isso exibe todo o conteúdo do arquivo. Também é possível juntar arquivos:

```bash
cat a.txt b.txt > combinado.txt
```

Já o comando `echo` é usado para exibir texto ou escrever em arquivos. Ele é muito utilizado em scripts:

```bash
echo "Olá mundo"
echo "Texto" > arquivo.txt
```

O primeiro imprime no terminal, o segundo grava no arquivo.

---

### Visualização eficiente de arquivos

Para arquivos grandes, usar `cat` não é ideal. Nesse caso, usamos:

```bash
less arquivo.txt
```

O `less` permite navegar pelo arquivo página por página, subir e descer, buscar palavras, etc.

Outros comandos úteis:

```bash
head arquivo.txt
```

Mostra as primeiras linhas (10 por padrão).

```bash
tail arquivo.txt
```

Mostra as últimas linhas, muito usado para logs.

```bash
tail -f arquivo.txt
```

Acompanha o arquivo em tempo real.

---

### Busca e padrões com grep

O comando `grep` é um dos mais importantes. Ele busca padrões dentro de arquivos.

```bash
grep "erro" log.txt
```

Isso mostra todas as linhas que contêm a palavra “erro”.

O grep pode usar **expressões regulares**, que são padrões avançados de busca. Por exemplo, buscar linhas que começam com determinada palavra ou seguem um formato específico.

---

### Processamento de texto com sed e awk

O `sed` é um editor de fluxo, muito usado para substituir texto automaticamente:

```bash
sed 's/erro/correto/g' arquivo.txt
```

Isso substitui todas as ocorrências de “erro” por “correto”.

Já o `awk` é mais poderoso e funciona como uma linguagem de programação para manipular dados estruturados, como colunas:

```bash
awk '{print $1}' arquivo.txt
```

Isso imprime a primeira coluna de cada linha.

---

### Ordenação e remoção de duplicados

Para organizar dados:

```bash
sort arquivo.txt
```

Ordena as linhas.

```bash
uniq arquivo.txt
```

Remove linhas duplicadas (geralmente usado junto com sort):

```bash
sort arquivo.txt | uniq
```

---

### Combinação de arquivos

O Linux permite combinar dados de várias formas.

O `paste` junta arquivos lado a lado:

```bash
paste arquivo1.txt arquivo2.txt
```

O `join` combina arquivos com base em um campo comum (como um ID), sendo muito usado em dados estruturados.

---

### Divisão de arquivos

Se um arquivo for muito grande, pode ser dividido com:

```bash
split -l 1000 arquivo.txt parte_
```

Isso divide o arquivo em partes de 1000 linhas.

---

### Transformação de caracteres

O comando `tr` é usado para transformar caracteres:

```bash
echo "abc" | tr 'a' 'x'
```

Saída: `xbc`

Também pode ser usado para converter letras:

```bash
echo "linux" | tr 'a-z' 'A-Z'
```

---

### Redirecionamento avançado

O comando `tee` permite salvar a saída e mostrar ao mesmo tempo:

```bash
ls | tee lista.txt
```

Isso exibe no terminal e salva no arquivo.

---

### Contagem e extração

O comando `wc` conta linhas, palavras e caracteres:

```bash
wc arquivo.txt
```

O `cut` extrai partes específicas:

```bash
cut -d ':' -f1 /etc/passwd
```

Isso extrai a primeira coluna usando “:” como separador.

---

### Trabalhando com arquivos binários

O comando `strings` extrai texto legível de arquivos binários:

```bash
strings programa
```

---

### Arquivos compactados

Existe uma família de comandos com prefixo `z` que permite trabalhar com arquivos compactados sem descompactar:

- `zcat`
- `zless`
- `zgrep`

Exemplo:

```bash
zgrep "erro" arquivo.gz
```
