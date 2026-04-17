# 🔹 Capítulo 13 – Manipulating Text

## 🔹 Tópicos
- cat e echo
- Trabalhando com Arquivos Grandes e Compactados
- sed e awk
- Utilitários de Manipulação de Arquivos (sort, uniq, paste, join, split)
- Expressões Regulares e Padrões de Busca
- grep e strings
- Utilitários Diversos de Texto (tr, tee, wc, cut)

---

## 🔹 Subtópicos

### A Eficiência da Linha de Comando
A linha de comando do Linux frequentemente permite que os usuários executem tarefas de manipulação e filtragem de texto de forma muito mais rápida e eficiente do que usando interfaces gráficas (GUI). Uma série de pequenos utilitários pode ser combinada para processar dados de maneira poderosa.

### cat e echo
- **cat (Concatenate):** É a ferramenta básica para ler, exibir no terminal (imprimir) e combinar (concatenar) o conteúdo de arquivos de texto. Pode ser usado para combinar três arquivos em um quarto arquivo. (Questão 13.1)
- **echo:** Um comando simples que exibe uma linha de texto na saída padrão (tela) ou é usado para inserir texto diretamente dentro de um arquivo. (Questão 13.2)

(abrir bash)
# Combinando arquivos:
cat arquivo1 arquivo2 arquivo3 > arquivo4

# Enviando texto para a tela:
echo "Texto de exemplo"
(fechar bash)

### Trabalhando com Arquivos Grandes e Compactados
Abrir arquivos gigantes em editores pode travar o sistema. O Linux oferece ferramentas para visualizar partes ou arquivos inteiros de forma paginada:
- **head:** Exibe as primeiras linhas de um arquivo (padrão 10 linhas).
- **tail:** Exibe as últimas linhas de um arquivo (padrão 10 linhas). Pode ser usado com as flags `-n15` ou `-15` para ver, por exemplo, as últimas 15 linhas. (Questão 13.3)
- **less:** Permite visualizar arquivos uma página por vez, permitindo rolagem para cima e para baixo.
- **Família de comandos 'z':** Ferramentas como `zcat` e `zless` usadas para trabalhar diretamente com arquivos compactados sem precisar descompactá-los primeiro.

(abrir bash)
# Ver as últimas 15 linhas de um arquivo:
tail -15 arquivo.txt
tail -n15 arquivo.txt
(fechar bash)

### sed e awk
- **sed (Stream Editor):** Editor de fluxo usado para filtrar e realizar substituições em arquivos. Para substituir todas as instâncias de uma palavra em uma linha, utiliza-se a flag `g` (global). Delimitadores diferentes de `/`, como `:`, também são aceitos. (Questão 13.4)
- **awk:** Linguagem de programação interpretada usada para extração de dados e relatórios. Utiliza delimitadores (flag `-F`) para fatiar linhas em campos (variáveis como $1, $2, $3). (Questão 13.5)

(abrir bash)
# Substituindo "dog" por "pig" globalmente:
sed -e s/dog/pig/g arquivo.txt
cat arquivo.txt | sed -e s/dog/pig/g

# Usando awk para imprimir a 1ª e 3ª coluna com delimitador ":":
awk -F: '{ print $1 $3 }' /usr/data/employee
(fechar bash)

### Utilitários de Manipulação de Arquivos
- **sort:** Organiza linhas em ordem ascendente ou descendente.
- **uniq:** Elimina entradas duplicadas (funciona melhor com o arquivo ordenado).
- **paste:** Combina campos de arquivos diferentes. A flag `-d` define um delimitador específico. (Questão 13.6)
- **join:** Combina linhas de dois arquivos que compartilham um campo comum. (Questão 13.7)
- **split:** Quebra um arquivo grande em segmentos de tamanhos iguais.

### Expressões Regulares e Busca (grep e strings)
Expressões regulares (Regex) são padrões usados para busca:
- **^**: Corresponde ao início de uma linha.
- **$**: Corresponde ao final de uma string/linha. (Questão 13.8)
- **grep:** Busca padrões em arquivos. Suporta classes de caracteres como `[0-5]` para buscar números específicos. (Questão 13.9)
- **grep -v:** Inverte a busca, imprimindo as linhas que **não** coincidem com o padrão. (Questão 13.10)
- **strings:** Extrai e exibe sequências de caracteres imprimíveis de arquivos binários. (Questão 13.11)

(abrir bash)
# Buscar linhas com números de 0 a 5:
grep [0-5] arquivo.txt
grep [0,1,2,3,4,5] arquivo.txt

# Ver apenas o que NÃO contém "erro":
grep -v "erro" log.txt
(fechar bash)

### Utilitários Diversos (tr, tee, wc, cut)
- **tr (Translate):** Traduz ou substitui caracteres individuais.
- **tee:** Salva uma cópia da saída padrão em um arquivo enquanto ainda a exibe no terminal.
- **wc (Word Count):** Exibe o número de linhas, palavras e caracteres.
- **cut:** Extrai colunas ou campos específicos de um arquivo para processamento. (Questão 13.12)

(abrir bash)
# Contando linhas de um arquivo:
wc -l arquivo.txt

# Extraindo a primeira coluna (campo) delimitada por vírgula:
cut -d"," -f1 arquivo.csv
(fechar bash)

---

# 🔹 Conteúdo

Neste capítulo, aprendi que a linha de comando do Linux supera a interface gráfica em eficiência para o processamento de dados. Comecei dominando o **cat** para combinar vários arquivos em um só e o **echo** para exibir textos ou criar arquivos rapidamente. Entendi que arquivos gigantes ou compactados não precisam ser um problema: uso o **less** para navegar, **head** e **tail** para focar em trechos específicos (como as últimas 15 linhas de um log) e a **família z** para ler arquivos zipados sem extração.

Mergulhei no poder do **sed** para substituições globais de texto e do **awk** para fatiar arquivos de dados complexos (como listas de funcionários) em colunas específicas usando delimitadores. Aprendi a organizar e limpar dados com **sort** e **uniq**, e a fundir arquivos diferentes usando o **paste** (lado a lado com delimitadores) ou o **join** (quando há um campo em comum).

Descobri como as Expressões Regulares facilitam a busca, usando o símbolo **$** para marcar o final de uma linha e colchetes para definir faixas de números. O comando **grep** se tornou essencial, especialmente com a flag **-v** para filtrar o que não me interessa, enquanto o **strings** me permitiu "espiar" textos dentro de arquivos binários. Por fim, conheci utilitários práticos como o **tr** para tradução de caracteres, o **wc** para estatísticas de arquivos, o **cut** para extrair colunas e o **tee**, que me permite gravar um log ao mesmo tempo em que acompanho a saída na tela.

---

# Comandos do Capítulo

| Comando | Descrição |
|--------|-----------|
| cat | Lê, imprime e combina arquivos (Questão 13.1). |
| echo | Exibe texto na saída padrão ou em arquivos (Questão 13.2). |
| head | Exibe as primeiras linhas de um arquivo (padrão 10). |
| tail | Exibe as últimas linhas de um arquivo (Questão 13.3). |
| less | Visualiza arquivos de forma paginada e navegável. |
| sed | Editor de fluxo para filtragem e substituição (Questão 13.4). |
| awk | Ferramenta de extração de dados e relatórios (Questão 13.5). |
| sort | Ordena linhas de texto de forma ascendente ou descendente. |
| uniq | Elimina linhas duplicadas consecutivas. |
| paste | Combina campos de arquivos diferentes (Questão 13.6). |
| join | Combina arquivos baseados em um campo comum (Questão 13.7). |
| split | Divide arquivos grandes em pedaços menores. |
| grep | Busca padrões usando expressões regulares (Questão 13.9 e 13.10). |
| strings | Extrai texto legível de arquivos binários (Questão 13.11). |
| tr | Traduz ou substitui caracteres individuais. |
| tee | Salva a saída em um arquivo e a exibe no terminal. |
| wc | Conta linhas, palavras e caracteres de um arquivo. |
| cut | Extrai colunas ou seções de um arquivo (Questão 13.12). |
| zcat/zless | Manipula arquivos de texto que estão compactados. |

---

# Explicação detalhada dos Comandos Básicos do Linux

## Visualização (head, tail e less)
O `head` e o `tail` são ideais para inspeções rápidas. O `tail -f` é especialmente famoso para monitorar logs em tempo real. O `less` é preferível ao `more` por permitir navegação total (setas para cima e para baixo) sem carregar o arquivo inteiro na memória.

## Processamento de Fluxo (sed e awk)
O `sed` trabalha linha por linha, sendo excelente para correções rápidas em scripts. O `awk` trata cada linha como um registro e cada palavra como um campo ($1, $2...), permitindo cálculos matemáticos e lógica de programação avançada sobre colunas de texto.

## Busca com Regex (grep e $)
O `grep` utiliza motores de busca de padrões. Aprender que o `$` âncora a busca no final da linha e que o `^` âncora no início é fundamental para evitar resultados falsos em buscas complexas.

## Manipulação de Colunas (cut, paste e join)
Enquanto o `cut` "fatia" um arquivo verticalmente para pegar uma coluna, o `paste` faz o oposto, "colando" arquivos horizontalmente. O `join` é o mais inteligente dos três, agindo como um "VLOOKUP" do Excel ou um JOIN de SQL, unindo linhas apenas se um ID ou campo for igual em ambos os arquivos.

---

## 🔹 Recursos úteis
- https://linuxcommand.org
- https://kernel.org
- https://gnu.org