# Capítulo 17 — Impressão no Linux (CUPS, PostScript e PDF)

No Linux, o sistema responsável pela impressão é o **CUPS (Common UNIX Printing System)**. Ele funciona como um servidor de impressão que recebe os arquivos enviados pelos programas, processa esses dados e os converte em um formato que a impressora consiga entender.

O CUPS oferece duas formas principais de interação pela linha de comando: os estilos **System V** e **BSD**, que são apenas formas diferentes de usar comandos para enviar arquivos para impressão. Independentemente do estilo, o funcionamento é o mesmo: você envia um arquivo, o CUPS coloca em uma fila e depois envia para a impressora.

Além da linha de comando, o CUPS também possui uma interface web acessível pelo navegador:

```bash
http://localhost:631
```

Nessa interface, é possível adicionar impressoras, gerenciar filas de impressão e acompanhar trabalhos em andamento. Isso facilita bastante a administração, principalmente em ambientes com várias impressoras.

---

Para imprimir diretamente pelo terminal, existem comandos simples como:

```bash
lp arquivo.txt
```

ou

```bash
lpr arquivo.txt
```

Ambos enviam o arquivo para a fila de impressão. Caso você queira escolher uma impressora específica ou configurar opções, pode usar:

```bash
lp -d nome_impressora arquivo.txt
```

O comando `lpoptions` permite definir configurações padrão, como tipo de papel, qualidade de impressão e outras opções, evitando precisar configurar toda vez.

---

Um conceito importante nesse processo é o uso do **PostScript (PS)**. Ele é uma linguagem usada para descrever páginas (texto, fontes e gráficos) de forma precisa. Isso permite que o conteúdo seja impresso com qualidade consistente, independentemente da impressora.

Por exemplo, um arquivo PostScript pode ser gerado a partir de um arquivo de texto usando:

```bash
enscript -p saida.ps arquivo.txt
```

O **enscript** converte texto simples em um formato que pode ser interpretado por impressoras ou convertido em outros formatos.

---

Hoje em dia, o formato mais utilizado é o **PDF (Portable Document Format)**. Ele garante que o documento será exibido e impresso da mesma forma em qualquer sistema, mantendo layout, fontes e imagens.

No Linux, existem várias ferramentas para trabalhar com PDFs. Uma das mais completas é o `pdftk`, que permite:

- juntar vários PDFs
- separar páginas
- proteger com senha
- corrigir arquivos corrompidos

Exemplo:

```bash
pdftk arquivo1.pdf arquivo2.pdf cat output final.pdf
```

Esse comando junta dois arquivos em um só.

---

Para obter informações sobre um PDF, usamos:

```bash
pdfinfo arquivo.pdf
```

Ele mostra dados como número de páginas, autor, tamanho e outras informações úteis.

---

Também existem ferramentas para edição e manipulação mais específica. O `flpsed` permite editar arquivos PostScript, enquanto o `pdfmod` oferece uma interface gráfica simples para modificar PDFs, como reorganizar páginas ou remover partes.

---

No geral, o sistema de impressão no Linux é bastante robusto e flexível. O CUPS centraliza todo o processo, enquanto ferramentas como `lp`, `enscript` e `pdftk` permitem desde tarefas simples até manipulações avançadas de documentos. Isso torna o Linux capaz de lidar com impressão tanto em ambientes domésticos quanto em ambientes corporativos complexos.