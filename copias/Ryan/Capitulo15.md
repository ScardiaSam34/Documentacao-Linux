# 🔹 Capítulo 15 – The Bash Shell and Basic Scripting

## 🔹 Tópicos Principais
- Fundamentos de Shell Scripting
- Sintaxe de Comandos (Quebras e Uniões)
- Valores de Retorno (Exit Status) e a variável $?
- Redirecionamento de Fluxo (I/O Redirection)
- Variáveis, Parâmetros Posicionais e Substituição de Comando
- Estruturas de Decisão (if/elif) e Testes de Sistema

---

## 🔹 Subtópicos Detalhados

### 1. O que é um Shell Script?
Um script é um arquivo de texto contendo uma sequência de comandos que o shell (interpretador) executa em ordem. O **bash** é o padrão no Linux.
- **O que pode conter:** Comandos embutidos do bash (built-ins), aplicativos compilados do sistema (como o `ls` ou `grep`) e até outros scripts.

### 2. Sintaxe e Formatação Profissional
Para manter o código legível e organizado, usamos dois caracteres fundamentais:
- **Barra Invertida (\):** Usada para continuar um comando muito longo na linha de baixo. (Questão 15.3)
- **Ponto e Vírgula (;):** Usado para colocar vários comandos na mesma linha. O shell executa o primeiro, espera terminar, e executa o próximo.

(abrir bash)
# Exemplo de múltiplos comandos:
cd /tmp ; touch aula_linux.txt ; ls -l
(fechar bash)

### 3. Valores de Retorno (Exit Status)
Todo comando, ao terminar, "cochicha" para o sistema um número.
- **0 (Zero):** Sucesso absoluto.
- **1 a 255:** Erro ou falha.
- **Variável $?:** É onde o bash guarda esse número do último comando executado. Fundamental para scripts tomarem decisões automáticas. (Questão 15.1)

### 4. Redirecionamento de Entrada e Saída (I/O)
- **Saída (> e >>):** Envia o resultado de um comando para um arquivo em vez da tela.
  - `>` : Sobrescreve (apaga o que tinha antes).
  - `>>` : Anexa (adiciona ao final, preservando o histórico). (Questão 15.7)
- **Entrada (<):** Faz um comando ler dados de um arquivo em vez de esperar que você digite no teclado.

(abrir bash)
# Salvando a lista de memória no log:
free >> /tmp/memoria_log.txt
(fechar bash)

### 5. Substituição de Comando (Command Substitution)
É a capacidade de usar a saída de um comando como se fosse um texto dentro de outro comando.
- **Sintaxe do Curso:** Crases ( `comando` ). (Questão 15.5)
- **Sintaxe Moderna (Recomendada):** `$(comando)`. Mais fácil de ler e permite aninhamento.

(abrir bash)
# Entrando em uma pasta baseada no resultado de um echo:
cd $(echo /var/log)
(fechar bash)

### 6. Variáveis e Parâmetros de Script
- **Variáveis de Ambiente:** São variáveis "globais" do sistema. Para que um script filho consiga ver uma variável criada pelo script pai, você deve usar o comando **export**.
- **Parâmetros Posicionais:** Capturam o que o usuário digitou ao chamar o script.
  - **$0**: Nome do próprio script. (Questão 15.6)
  - **$1, $2...**: Primeiro, segundo argumento, etc.
  - **$***: Pega todos os argumentos de uma vez.

### 7. Estruturas Condicionais (if / elif)
O `if` testa uma condição. Se for verdade, executa o `then`. O `elif` permite testar uma segunda ou terceira opção se a primeira falhar.
- **Operador NOT (!):** Inverte o teste. Se algo não existe, por exemplo. (Questão 15.11)

**Testes de Arquivos (Atributos):**
- **-e**: Verifica se o caminho existe. (Questão 15.10)
- **-d**: Verifica se é um **diretório**. (Questão 15.12)
- **-f**: Verifica se é um arquivo comum.
- **-r**: Verifica se o arquivo pode ser lido pelo usuário.

**Comparações de Texto (Strings):**
- **Bash do Curso (Clássico):** `[ $A == $B ]` ou `[ $A = $B ]`. (Questão 15.9)
- **Bash Atual (Robusto):** `[[ $A == $B ]]`. O uso de colchetes duplos evita muitos erros de sintaxe quando variáveis estão vazias.

**Comparações Numéricas:**
Não usamos sinais matemáticos em colchetes simples para números. Usamos siglas:
- **-eq**: Igual (Equal).
- **-gt**: Maior que (Greater Than).
- **-lt**: Menor que (Less Than).

### 8. Matemática no Bash
- **expr:** Utilitário externo. Ex: `expr 2 + 3`. (Questão 15.8)
- **let:** Comando interno para cálculos e atribuições. Ex: `let x=(1+5)`.

### 9. Permissões e Execução
Existem duas formas de rodar seu script:
1. **Manual:** `bash script.sh` (Não precisa de permissão especial, o bash lê o arquivo como texto). (Questão 15.2)
2. **Independente:** `./script.sh`. Para isso, você **precisa** dar permissão de execução: `chmod +x script.sh`. (Questão 15.1)

---

# 🔹 Resumo das "Cascas de Banana" (Fixação)

Neste capítulo, entendi que um script é uma ferramenta de automação poderosa. Aprendi que para um script ser "independente" e rodar com `./`, ele precisa do **chmod +x**. Se eu esquecer a permissão, ainda posso forçar a execução chamando o interpretador `bash` diretamente.

Dominei a arte de não poluir a tela: uso o **redirecionamento** para guardar logs importantes, preferindo o **>>** para nunca perder dados antigos. Aprendi que o bash tem um "diário" secreto chamado **$?** que me diz se o último comando deu certo (0) ou errado.

Na parte de lógica, agora sei que o bash trata texto e número de formas diferentes: uso `==` para palavras e `-eq` para números. Descobri que o **$0** é o nome do meu script e que, para testar se uma pasta existe antes de tentar entrar nela, o operador correto é o **-d**. Por fim, aprendi a usar o **export** para garantir que minhas variáveis não morram dentro do script e possam ser vistas por outros programas que eu chamar.

---

# Comandos Rápidos (Gabarito de Bolso)

| Comando | O que faz (Foco no Quiz) |
| :--- | :--- |
| `chmod +x` | Torna o script executável (Questão 15.1). |
| `bash script.sh` | Roda o script manualmente (Questão 15.2). |
| `\` | Continua o comando na linha de baixo (Questão 15.3). |
| `$( )` ou `` ` ` `` | Substituição de comando (Questão 15.5). |
| `$0` | Variável com o nome do script (Questão 15.6). |
| `>>` | Anexa saída ao arquivo (Questão 15.7). |
| `expr` ou `let` | Realiza cálculos matemáticos (Questão 15.8). |
| `[ $A == $B ]` | Compara strings no bash clássico (Questão 15.9). |
| `-d` | Testa se é um diretório (Questão 15.12). |
| `!` | Operador lógico NOT (Questão 15.11). |

---
## 🔹 Recursos úteis
- https://linuxcommand.org 
- https://kernel.org 
- https://gnu.org