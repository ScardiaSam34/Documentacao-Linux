# Capítulo 8 — Encontrando documentação do Linux

No Linux, uma das coisas mais importantes é saber **como buscar ajuda sozinho dentro do próprio sistema**. Diferente de outros sistemas operacionais, o Linux foi feito para ser bem documentado, principalmente via terminal. Isso significa que praticamente todo comando, programa ou recurso possui uma explicação acessível diretamente no sistema.

A principal forma de documentação são as chamadas **man pages (manual pages)**. Elas são acessadas com o comando:

```bash
man comando
```

Por exemplo:

```bash
man ls
```

Esse comando abre uma página completa explicando tudo sobre o `ls`, incluindo descrição, opções, exemplos e funcionamento. Essas páginas são organizadas em seções (como comandos, arquivos, chamadas do sistema, etc.), e são extremamente detalhadas. Em muitos casos, tudo que você precisa saber já está ali.

Dentro do `man`, você pode navegar usando o teclado:

- `↑ ↓` para rolar
- `/palavra` para buscar
- `q` para sair

Além do `man`, existe o sistema **GNU Info**, acessado com:

```bash
info comando
```

Ele é mais estruturado em forma de navegação (como um menu com links), sendo útil para documentações mais longas e organizadas.

---

## Ajuda rápida de comandos

Nem sempre você precisa abrir uma documentação completa. Muitos comandos possuem ajuda rápida integrada, usando:

```bash
comando -h
```

ou

```bash
comando --help
```

Exemplo:

```bash
ls --help
```

Isso mostra um resumo das opções disponíveis, de forma mais direta e rápida do que o `man`.

---

## Comando help (interno do shell)

O próprio shell (como o bash) possui comandos internos. Para ver ajuda deles, usa-se:

```bash
help
```

Ou para um comando específico:

```bash
help cd
```

Isso é importante porque alguns comandos não têm `man`, já que fazem parte do próprio shell.