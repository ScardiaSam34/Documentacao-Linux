# Capítulo 16 — Mais sobre scripts Bash Shell

Neste capítulo, o shell scripting evolui para um nível mais avançado, permitindo trabalhar melhor com dados, tomar decisões mais complexas e criar scripts mais inteligentes e seguros.

Um dos pontos principais é a **manipulação de strings**. No bash, strings são simplesmente textos armazenados em variáveis, mas podem ser manipuladas de várias formas. É possível comparar valores, verificar tamanho e até extrair partes específicas.

Por exemplo, comparar duas strings:

```bash
if [[ "$nome" == "Maria" ]]; then
  echo "Nome correto"
fi
```

Também é possível descobrir o tamanho de uma string:

```bash
texto="Linux"
echo ${#texto}
```

Isso retorna a quantidade de caracteres. Já para extrair partes:

```bash
echo ${texto:0:3}
```

Nesse caso, seriam exibidos apenas os três primeiros caracteres.

---

Outro conceito importante são as **expressões booleanas**, que sempre resultam em verdadeiro ou falso. Elas são usadas em condições e decisões dentro do script.

Os principais operadores são:

- `&&` (E lógico) → ambas condições devem ser verdadeiras
- `||` (OU lógico) → pelo menos uma deve ser verdadeira
- `!` (NÃO) → inverte o valor

Exemplo prático:

```bash
if [[ $idade -ge 18 && $idade -le 60 ]]; then
  echo "Idade válida"
fi
```

---

Quando existem muitas opções possíveis, usar vários `if` pode ficar confuso. Para isso existe a estrutura **case**, que organiza melhor as decisões.

Exemplo:

```bash
case $opcao in
  1) echo "Você escolheu 1" ;;
  2) echo "Você escolheu 2" ;;
  *) echo "Opção inválida" ;;
esac
```

Isso torna o código mais limpo e fácil de entender.

---

Outro ponto essencial é a **depuração de scripts**, ou seja, encontrar e corrigir erros. O bash permite executar scripts em modo de debug, mostrando cada comando sendo executado.

Exemplo:

```bash
bash -x script.sh
```

Ou dentro do próprio script:

```bash
set -x
 # comandos aqui
set +x
```

Isso ajuda a entender exatamente onde está o problema.

---

O controle de **entrada e saída** também é muito importante. Todo comando no Linux trabalha com três fluxos:

- `stdin (0)` → entrada
- `stdout (1)` → saída normal
- `stderr (2)` → erros

Você pode redirecionar esses fluxos:

```bash
comando > saida.txt
```

Salva a saída normal.

```bash
comando 2> erro.txt
```

Salva apenas erros.

```bash
comando > tudo.txt 2>&1
```

Salva tudo no mesmo arquivo.

Isso é muito útil para logs e depuração.

---

O Linux também permite trabalhar com **arquivos temporários**, que são usados para armazenar dados por pouco tempo. Eles são importantes para segurança, pois evitam conflitos e acessos indevidos.

A forma correta de criar é:

```bash
temp=$(mktemp /tmp/arquivo.XXXXXX)
```

Isso garante um nome único e seguro.

---

Outro recurso interessante é o uso de **/dev/null**, que funciona como um “buraco negro”: tudo que é enviado para ele é descartado.

Exemplo:

```bash
ls /tmp > /dev/null
```

Aqui, a saída é ignorada.

```bash
ls /tmp > /dev/null 2>&1
```

Ignora tanto saída quanto erro.

---

Por fim, o Linux permite gerar **números aleatórios**, algo muito útil para scripts, testes e segurança.

Exemplo simples:

```bash
echo $RANDOM
```

Isso gera um número aleatório a cada execução.

Também existem fontes mais avançadas:

- `/dev/random` → mais seguro, porém lento
- `/dev/urandom` → mais rápido e mais usado

