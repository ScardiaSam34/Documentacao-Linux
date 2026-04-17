# 🔹 Capítulo 11 – Text Editors

## 🔹 Tópicos
- Editores Básicos: nano e gedit
- Editores Avançados: vi e emacs

---

## 🔹 Subtópicos

### Visão Geral dos Editores de Texto
No Linux, editores de texto são ferramentas fundamentais. Diferente de processadores de texto (como o Microsoft Word, que adicionam formatação invisível e estilos), os editores de texto lidam com texto puro (plain text). Eles são usados rotineiramente para criar ou modificar arquivos de configuração do sistema, escrever scripts e desenvolver código-fonte.

### Criando Arquivos Sem um Editor
Antes mesmo de abrir um editor, é possível criar arquivos de texto diretamente pela linha de comando usando ferramentas de redirecionamento. Comandos como `touch` criam arquivos vazios, enquanto redirecionamentos como `echo "texto" > arquivo.txt` ou `cat > arquivo.txt` permitem inserir conteúdo rapidamente sem precisar iniciar uma interface de edição.

### Editores Básicos: nano e gedit
Para edições rápidas e para iniciantes, o Linux oferece opções bastante amigáveis:
- **nano:** É um editor baseado em texto (CLI) extremamente fácil de usar. Ele exibe os atalhos de teclado na parte inferior da tela (usando a tecla `Ctrl`, representada por um acento circunflexo `^`, como `^O` para salvar e `^X` para sair), eliminando a necessidade de memorizar comandos complexos.
- **gedit:** É um editor gráfico (GUI) padrão em muitos ambientes desktop Linux (como o GNOME). Ele funciona de maneira muito semelhante ao Bloco de Notas (Notepad) do Windows, permitindo o uso do mouse, menus e atalhos convencionais (`Ctrl+S`, `Ctrl+C`).
- **Visual Studio Code (VS Code):** Mencionado como uma alternativa moderna e poderosa, é um editor de código-fonte gráfico altamente extensível, muito popular entre desenvolvedores para escrever scripts e programar.

### Editores Avançados: vi e emacs
Para máxima eficiência e produtividade, administradores de sistemas e programadores utilizam editores avançados. A curva de aprendizado é íngreme, mas, uma vez dominados, permitem editar textos de forma extremamente rápida sem tirar as mãos do teclado.

**Introdução ao vi (e vim):**
O **vi** (Visual Editor) ou sua versão melhorada **vim** (Vi IMproved) está presente em praticamente todos os sistemas Linux (padrão POSIX), tornando-se uma habilidade essencial. Para aprender a usá-lo, o sistema oferece um tutorial interativo acessível pelo comando **`vimtutor`**.

**Os 3 Modos do vi:**
O `vi` é um editor modal, o que significa que as teclas do seu teclado fazem coisas diferentes dependendo do modo em que você está:
1. **Command Mode (Modo de Comando / Normal):** É o modo padrão ao abrir um arquivo. Aqui, as letras não digitam texto, mas atuam como comandos de movimentação (como usar `h`, `j`, `k`, `l` como setas), exclusão, cópia e colagem.
2. **Insert Mode (Modo de Inserção):** Usado para efetivamente digitar texto no arquivo. Você entra neste modo pressionando teclas como `i` (insert) ou `a` (append). Para sair e voltar ao Modo de Comando, pressiona-se a tecla `Esc`.
3. **Line / Ex Mode (Modo de Linha / Última Linha):** Acessado a partir do Modo de Comando digitando `:` (dois pontos) ou `/` (barra para busca). Usado para salvar o arquivo, fechar o editor, buscar palavras ou executar comandos externos.

**Introdução ao emacs:**
O **emacs** é a principal e mais popular alternativa ao `vi`. Ele pode rodar tanto no terminal (texto) quanto com uma interface gráfica (GUI). O tutorial embutido pode ser acessado pressionando `Ctrl-h` seguido da tecla `t`.
Diferente do `vi`, o `emacs` **não possui modos distintos** para comandos e inserção. Você sempre está no modo de digitação. Para enviar comandos (como salvar ou mover o cursor rapidamente), você usa combinações (acordes) de teclas especiais, principalmente a tecla `Control` (C) e a tecla `Meta` (frequentemente mapeada para o `Alt` ou `Escape`).

---

# 🔹 Conteúdo

Neste capítulo, aprendi que os editores de texto são ferramentas indispensáveis no Linux, muito diferentes dos processadores de texto convencionais, pois trabalham exclusivamente com texto puro. Entendi que eles são a base para configurar o sistema, programar e escrever scripts. Também descobri que posso criar arquivos rapidamente na linha de comando sem sequer abrir um editor, usando redirecionamentos simples.

Comecei explorando as opções mais amigáveis. Conheci o **nano**, um editor de terminal perfeito para iniciantes, pois exibe todos os atalhos necessários na própria tela, guiando o usuário passo a passo. No ambiente gráfico, vi que o **gedit** oferece uma experiência familiar, quase idêntica ao Bloco de Notas, enquanto o **Visual Studio Code** atende a demandas mais complexas de desenvolvimento com uma interface moderna.

O grande foco, no entanto, foi o mergulho nos editores avançados clássicos: **vi** e **emacs**. Entendi que o `vi` é universal, estando disponível em qualquer servidor Linux que eu venha a acessar. Descobri que ele funciona através de três modos distintos: o Modo de Comando (para navegar e manipular blocos de texto), o Modo de Inserção (para digitar) e o Modo de Linha (para salvar e sair). Aprendi que a transição fluida entre esses modos, utilizando a tecla `Esc`, é o segredo da eficiência no `vi`.

Também fui apresentado ao **emacs**, seu histórico concorrente. Ao contrário do `vi`, o `emacs` possui apenas um modo de operação contínua, exigindo que as ações de edição e salvamento sejam feitas através de combinações simultâneas de teclas, como `Control` e `Alt` (Meta). 

Embora ambos exijam dedicação e tenham uma curva de aprendizado longa, aprendi que dominar os atalhos e a navegação desses editores — e usar ferramentas de apoio como o `vimtutor` — transforma completamente a velocidade e a eficiência com que administro um sistema Linux.

---

# Comandos do Capítulo

| Comando | Descrição |
|--------|-----------|
| `nano` | Inicia o editor de texto simples baseado em terminal. |
| `gedit` | Inicia o editor de texto gráfico padrão do ambiente GNOME. |
| `code` | Comando comum para iniciar o Visual Studio Code (se instalado). |
| `vi` / `vim` | Inicia o editor de texto avançado modal padrão do Linux. |
| `vimtutor` | Abre um tutorial prático e interativo no terminal para aprender a usar o `vi/vim`. |
| `emacs` | Inicia o editor de texto avançado baseado em combinações de teclas. |
| `cat >` | Permite criar um arquivo e digitar conteúdo diretamente do terminal até pressionar `Ctrl+D`. |

# Explicação detalhada dos Comandos Básicos do Linux

## nano
O editor mais fácil para edições rápidas no terminal. Ao digitar `nano arquivo.txt`, a interface ocupa a tela. Você simplesmente digita o texto normalmente.
- **Para Salvar:** Pressione `Ctrl + O` (Write Out), confirme o nome do arquivo com `Enter`.
- **Para Sair:** Pressione `Ctrl + X`. Se houver alterações não salvas, ele perguntará se deseja salvar antes de sair.

## vi / vim (Comandos Essenciais)
Para usar o `vi`, é crucial entender a mudança de modos. Ao abrir o editor (`vi arquivo.txt`), você entra no **Modo de Comando** por padrão.
- **Para começar a digitar (ir para o Insert Mode):** Pressione `i` (inserir antes do cursor) ou `a` (inserir depois do cursor). A palavra `-- INSERT --` aparecerá na base da tela.
- **Para parar de digitar e voltar a enviar comandos:** Pressione `Esc`.
- **Navegação (no Modo de Comando):** Use `h` (esquerda), `j` (baixo), `k` (cima), `l` (direita), ou as setas do teclado.
- **Exclusão (no Modo de Comando):** Pressione `dd` para apagar uma linha inteira ou `x` para apagar um caractere.
- **Para Salvar e Sair (Modo de Linha):** A partir do modo de comando, digite `:` para ir para a última linha, depois digite `wq` (write and quit) e pressione `Enter`. Para sair sem salvar (forçar saída), digite `:q!`.

## emacs (Comandos Essenciais)
O `emacs` usa uma notação específica para seus atalhos. `C` significa `Control` e `M` significa `Meta` (geralmente `Alt` ou `Esc`).
- Para acessar o tutorial: Pressione `Ctrl + h`, solte, e aperte `t` (`C-h t`).
- Para salvar um arquivo: Pressione `Ctrl + x` seguido de `Ctrl + s` (`C-x C-s`).
- Para sair do emacs: Pressione `Ctrl + x` seguido de `Ctrl + c` (`C-x C-c`).
- O emacs é contínuo, ou seja, se você digitar letras normais, elas simplesmente aparecerão no documento, não há necessidade de apertar `i` como no vi.

---

## 🔹 Recursos úteis
https://linuxcommand.org 
https://kernel.org 
https://gnu.org