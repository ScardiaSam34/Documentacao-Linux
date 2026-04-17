# Manipulação de Texto e Fluxos de Dados no Linux
## 1. Exibição e Redirecionamento (`cat` e `echo`)

Essas ferramentas são a base para mover texto entre comandos e arquivos.

* **`cat` (Concatenate):**
    * **Visualizar:** `cat arquivo.txt` exibe todo o conteúdo.
    * **Anexar:** `cat arquivo1.txt >> arquivo_destino.txt` adiciona o conteúdo de um arquivo ao final de outro.
* **`echo`:**
    * **Criar/Sobrescrever:** `echo "Texto" > arquivo.txt` cria um arquivo com o conteúdo (ou apaga o que existia).
    * **Anexar:** `echo "Nova linha" >> arquivo.txt` adiciona o texto ao final do arquivo sem apagar o anterior.

---

## 2. Busca de Padrões com `grep`

O `grep` (Global Regular Expression Print) é a ferramenta definitiva para encontrar texto.

* **Busca simples:** `grep "palavra" arquivo.txt`
* **Ignorar maiúsculas/minúsculas:** `grep -i "texto" arquivo.txt`
* **Busca recursiva em diretórios:** `grep -r "configuracao" /etc/`
* **Inverter a busca:** `grep -v "erro" log.txt` (mostra tudo que **não** contém "erro").
* **Contar ocorrências:** `grep -c "usuario" lista.txt`

---

## 3. Edição Não-Interativa com `sed`

O `sed` (Stream Editor) permite transformar texto em fluxos de dados sem abrir o arquivo manualmente.

* **Substituição simples:** `sed 's/antigo/novo/' arquivo.txt` (muda apenas a primeira ocorrência da linha).
* **Substituição global:** `sed 's/antigo/novo/g' arquivo.txt` (muda todas as ocorrências).
* **Remover linhas:** `sed '3d' arquivo.txt` (deleta a terceira linha).
* **Edição no próprio arquivo:** `sed -i 's/localhost/127.0.0.1/g' config.conf` (salva a alteração permanentemente).

---

## 4. Processamento de Colunas com `awk`

O `awk` é uma linguagem de programação completa para processar dados estruturados em colunas/campos.

* **Imprimir colunas específicas:** `awk '{print $1, $3}' arquivo.txt` (imprime a 1ª e a 3ª coluna).
* **Filtrar por valor de coluna:** `awk '$3 > 100 {print $1}' dados.txt` (imprime a 1ª coluna se a 3ª for maior que 100).
* **Definir delimitador personalizado:** `awk -F":" '{print $1}' /etc/passwd` (usa ":" como separador, comum em arquivos de sistema).

---

## 5. Outras Ferramentas de Manipulação

O ecossistema Linux possui pequenos utilitários que resolvem problemas específicos de forma rápida.

* **`sort`:** Ordena as linhas alfabética ou numericamente.
    * `sort -n arquivo.txt` (ordem numérica).
* **`uniq`:** Remove ou identifica linhas duplicadas.
    * `sort arquivo.txt | uniq` (remove duplicados de uma lista ordenada).
* **`wc` (Word Count):** Conta linhas, palavras e caracteres.
    * `wc -l arquivo.txt` (conta apenas o número de linhas).
* **`cut`:** Recorta partes específicas das linhas.
    * `cut -c 1-10 arquivo.txt` (extrai apenas os primeiros 10 caracteres).
* **`tr` (Translate):** Traduz ou deleta caracteres.
    * `cat arquivo.txt | tr 'a-z' 'A-Z'` (converte tudo para maiúsculas).
* **`head` / `tail`:**
    * `head -n 5`: Mostra as 5 primeiras linhas.
    * `tail -f log.txt`: Acompanha as novas linhas adicionadas a um arquivo em tempo real (muito usado para monitorar logs).

---

## 6. O Poder do Pipe (`|`)

O verdadeiro poder dessas ferramentas surge quando elas são combinadas. O símbolo `|` (pipe) envia a saída de um comando para a entrada do próximo.

**Exemplo:** Filtrar os 5 processos que mais consomem memória, ordená-los e salvar em um arquivo.
```bash
ps aux | sort -nk 4 | tail -n 5 > top_processos.txt