# Capítulo 15 — O Shell Bash e a Programação Básica de Scripts

Shell scripting no Linux é a forma de **automatizar tarefas** usando arquivos que contêm vários comandos que normalmente seriam digitados manualmente no terminal. Esses arquivos são chamados de *scripts* e geralmente são executados pelo shell, sendo o mais comum o **bash**.

Na prática, um script nada mais é do que uma sequência de comandos organizados em um arquivo. Em vez de executar comandos um por um, você escreve tudo uma vez e depois executa automaticamente. Isso é muito útil para tarefas repetitivas, como backups, instalação de programas ou processamento de arquivos.

Todo script normalmente começa com o chamado *shebang*, que indica qual interpretador será usado:

```bash
#!/bin/bash
```

Depois disso, você pode escrever comandos normalmente:

```bash
#!/bin/bash
echo "Olá, mundo!"
```

Para executar, é necessário dar permissão:

```bash
chmod +x script.sh
./script.sh
```

---

Um conceito muito importante é o uso de **variáveis**, que permitem armazenar valores dentro do script. Isso torna o script mais dinâmico e reutilizável.

Exemplo:

```bash
nome="João"
echo "Olá $nome"
```

Também é possível receber dados do usuário:

```bash
read nome
echo "Bem-vindo $nome"
```

---

Outro recurso essencial é a **substituição de comandos**, que permite usar o resultado de um comando dentro de outro. Isso torna os scripts muito mais poderosos.

Exemplo:

```bash
echo "Você está no diretório $(pwd)"
```

Aqui, o comando `pwd` é executado e seu resultado é inserido dentro do `echo`.

---

Os scripts também podem receber **parâmetros**, ou seja, valores passados na hora da execução.

Exemplo:

```bash
./script.sh Maria
```

Dentro do script:

```bash
echo "Olá $1"
```

O `$1` representa o primeiro argumento. Existem outros como `$2`, `$#` (quantidade de argumentos) e `$*` (todos os argumentos).

---

O **redirecionamento** é outro conceito fundamental. Ele permite controlar de onde vêm os dados e para onde vão.

Exemplos:

```bash
echo "Texto" > arquivo.txt
```

Aqui, a saída é enviada para um arquivo (sobrescrevendo).

```bash
echo "Mais texto" >> arquivo.txt
```

Adiciona conteúdo ao arquivo.

```bash
cat < arquivo.txt
```

Usa um arquivo como entrada.

Também existe o uso de pipes:

```bash
cat arquivo.txt | grep "erro"
```

Nesse caso, a saída de um comando vira entrada de outro.

---

As **condicionais** permitem que o script tome decisões com base em condições. A estrutura mais comum é o `if`.

Exemplo:

```bash
if [ -f arquivo.txt ]; then
  echo "Arquivo existe"
else
  echo "Arquivo não existe"
fi
```

Aqui, o script verifica se o arquivo existe antes de executar uma ação.

---

Outro ponto importante são as **expressões aritméticas**, que permitem fazer cálculos dentro do script.

Exemplo:

```bash
resultado=$((5 + 3))
echo $resultado
```

Isso é útil para contadores, loops e cálculos simples.

---

As **funções** permitem organizar o código e reutilizar partes do script. Elas funcionam como blocos de comandos que podem ser chamados quando necessário.

Exemplo:

```bash
minha_funcao() {
  echo "Executando função"
}

minha_funcao
```

---

As **variáveis de ambiente** são valores definidos pelo sistema ou pelo usuário que influenciam o comportamento dos programas. Exemplos comuns são:

- `$HOME` → diretório do usuário
- `$PATH` → onde o sistema procura programas

Se você quiser que uma variável seja acessível por outros processos (como scripts chamados dentro do seu script), é necessário exportar:

```bash
export VAR=valor
```

---

Por fim, todo script retorna um **valor de saída**, chamado de *status code*. O valor `0` significa sucesso, enquanto qualquer outro valor indica erro.

Você pode verificar o último código com:

```bash
echo $?
```