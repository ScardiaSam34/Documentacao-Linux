# 🔹 Capítulo 17 – Printing & Advanced Shell Scripting

## 🔹 Tópicos
- O Sistema de Impressão CUPS (Common UNIX Printing System)
- Operações de Impressão via CLI (Interface de Linha de Comando)
- Manipulação de Arquivos PostScript e PDF
- Automação Avançada: Loops, Case e Manipulação de Strings
- Depuração e Técnicas de Scripting (mktemp, /dev/null, $RANDOM)

---

## 🔹 Subtópicos

### O Sistema CUPS e Configuração
O CUPS é o padrão para impressão no Linux. Ele gerencia o fluxo desde o pedido do usuário até o hardware.
- **Funcionalidades:** Pode conectar impressoras locais e compartilhá-las na rede, além de conectar o Linux a impressoras de rede já existentes.
- **Interfaces:** O CUPS oferece as interfaces de comando **System V** e **BSD**.
- **Painel Web:** A administração completa (adicionar, pausar ou remover impressoras) está disponível em **localhost:631**.
- **Arquitetura:** Trabalha com um agendador (**Scheduler**), arquivos de configuração, logs e filtros que traduzem o documento para a linguagem da impressora.

### Operações de Impressão e PDF
- **Comandos de Envio:** **lp** e **lpr** submetem documentos à fila.
- **Preferências:** O comando **lpoptions** é usado para definir opções e impressoras padrão (ex: `lpoptions -d NOME_IMPRESSORA`).
- **PostScript (PS):** Formato que escala fontes e gráficos vetoriais perfeitamente. O utilitário **enscript** converte texto puro para PS. O **flpsed** permite adicionar dados a documentos PS.
- **PDF (Portable Document Format):** Padrão para troca consistente de documentos.
  - **pdfinfo:** Extrai metadados do arquivo.
  - **pdfmod:** Interface gráfica (GUI) para modificar PDFs.
  - **pdftk:** O canivete suíço (junta, divide, criptografa, repara e preenche formulários).
  - **qpdf:** Ferramenta poderosa para transformações estruturais e mesclagem de arquivos.

### Shell Scripting: Estruturas de Decisão e Repetição
- **Manipulação de Strings:** O Bash mede o tamanho de strings com `${#variavel}` e extrai partes do texto (substrings).
- **Operadores Lógicos:** **&&** (AND), **||** (OR) e **!** (NOT) permitem criar condições complexas.
- **Estrutura case:** Substitui múltiplos "if/elif" por uma comparação de padrões (patterns) mais limpa.
- **Loops (Repetição):**
  - **for:** Itera sobre listas de itens (arquivos, palavras).
  - **while:** Executa enquanto uma condição for verdadeira.
  - **until:** Executa até que uma condição se torne verdadeira.

### Depuração e Boas Práticas
- **Debugging:** Ativado com **bash -x** ou **set -x** dentro do script para ver a execução passo a passo.
- **Redirecionamento:** O código de erro (Standard Error) é o **2**. Pode ser enviado para um arquivo (`2> erro.log`) ou para o "buraco negro" (**2> /dev/null**).
- **Arquivos Temporários:** O comando **mktemp** cria arquivos ou diretórios únicos de forma segura.
- **Aleatoriedade:** A variável **$RANDOM** gera números aleatórios para uso em scripts.

---

# 🔹 Conteúdo

Neste capítulo, dominei as engrenagens da impressão no Linux e a automação avançada via Shell. Entendi que o **CUPS** é a central de tudo, permitindo gerenciar impressoras locais e de rede, inclusive através da interface web em **localhost:631**. Aprendi a controlar a fila de impressão pelo terminal com **lp** e a definir minha impressora padrão usando **lpoptions -d**, o que facilita muito o fluxo de trabalho sem depender de interfaces gráficas.

Aprofundei-me na manipulação de documentos, vendo como o **PostScript** preserva a qualidade visual e como ferramentas como o **enscript** e **pdftk** são essenciais. O ponto alto foi aprender a manipular PDFs via linha de comando: agora sei que para consolidar vários relatórios em um único arquivo, posso usar tanto o `pdftk` com o parâmetro `cat output`, quanto o `qpdf` com a sintaxe `--empty --pages`. Além disso, o `pdfinfo` se mostrou vital para espiar os metadados dos documentos.

Na parte de scripting, evoluí minha lógica de programação. Aprendi a lidar com strings e a usar operadores lógicos para criar condições inteligentes. Substituí blocos de código confusos pela estrutura **case**, tornando meus scripts de menu muito mais profissionais. Dominei o uso de **loops** (for, while e until) para automação de tarefas repetitivas e aprendi que um bom administrador sempre sabe depurar seu código com `set -x` e lidar com mensagens de erro indesejadas enviando-as para o `/dev/null`. Técnicas como o uso de arquivos temporários seguros com `mktemp` e a geração de dados aleatórios com `$RANDOM` completaram meu arsenal de desenvolvedor Linux.

---

# Comandos e Operadores do Capítulo

| Operador / Comando | Descrição |
|--------|-----------|
| `lpoptions -d` | Define a impressora padrão do sistema (Cobrado no Quiz). |
| `pdftk A.pdf B.pdf cat output ABC.pdf` | Combina vários PDFs em um arquivo final (Cobrado no Quiz). |
| `qpdf --empty --pages A.pdf B.pdf -- ABC.pdf` | Alternativa para mesclar (merge) arquivos PDF (Cobrado no Quiz). |
| `localhost:631` | Endereço da interface web de administração do CUPS. |
| `lp` / `lpr` | Submetem documentos para impressão via CLI. |
| `pdfinfo` | Extrai informações técnicas e metadados de um PDF. |
| `enscript` | Converte arquivos de texto para PostScript. |
| `case` / `esac` | Condicional de múltipla escolha por padrões. |
| `for` / `while` / `until` | Estruturas de repetição (Loops). |
| `2> /dev/null` | Descarta apenas as mensagens de erro de um comando. |
| `mktemp` | Cria arquivos temporários de forma segura. |
| `$RANDOM` | Gera números aleatórios. |

# Explicação Detalhada e Exemplos

## Configurando a Impressora Padrão
Se você tem várias impressoras, mas quer que o sistema use sempre a mesma sem perguntar:
(abrir bash)
lpoptions -d MFC9340CDW
(fechar bash)

## Mesclando Documentos PDF (As duas formas corretas)
O questionário exige que você conheça ambas as sintaxes para combinar arquivos.
(abrir bash)
# Usando pdftk:
pdftk documento1.pdf documento2.pdf cat output final.pdf

# Usando qpdf:
qpdf --empty --pages documento1.pdf documento2.pdf -- final.pdf
(fechar bash)

## O Loop While e Redirecionamento de Erro
(abrir bash)
# Loop que roda enquanto o contador for menor que 5, 
# jogando erros de comandos inexistentes para o lixo:
CONTADOR=1
while [ $CONTADOR -lt 5 ]; do
    comando_que_nao_existe 2> /dev/null
    echo "Contagem: $CONTADOR"
    CONTADOR=$((CONTADOR + 1))
done
(fechar bash)

---

## 🔹 Recursos úteis
- https://linuxcommand.org 
- https://kernel.org 
- https://gnu.org