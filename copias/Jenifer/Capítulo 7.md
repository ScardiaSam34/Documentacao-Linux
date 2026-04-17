# Capítulo 7 — Operações de Linha de Comando

O Linux pode ser utilizado tanto por interface gráfica quanto por terminal, mas **o terminal é uma das ferramentas mais poderosas do sistema**. Ele permite executar comandos diretamente, oferecendo mais controle sobre o funcionamento do sistema.

Um dos conceitos importantes são os **terminais virtuais (VTs)**. Eles são consoles em modo texto que utilizam diretamente o teclado e o monitor do computador, sem depender da interface gráfica. Isso significa que mesmo que o ambiente gráfico falhe, ainda é possível acessar o sistema. Esses terminais podem ser acessados com atalhos como:

```bash
Ctrl + Alt + F3
```

Já dentro do ambiente gráfico, existem os **emuladores de terminal**, que simulam esse terminal em uma janela, permitindo usar comandos sem sair da interface visual.

O Linux permite fazer login tanto localmente, em um terminal de texto, quanto remotamente, através de conexões de rede. Um detalhe importante de segurança é que, ao digitar a senha, nada aparece na tela nem mesmo asteriscos para evitar que outras pessoas saibam o tamanho da senha.

<div style="border-left: 4px solid #555; padding-left: 10px; margin: 10px 0;"> Para desligar ou reiniciar o sistema corretamente, o método recomendado é utilizar o comando:
</div>

```bash
sudo shutdown now
```

ou para reiniciar:

```bash
sudo shutdown -r now
```

Isso garante que todos os processos sejam encerrados corretamente.

Outro conceito essencial é o de **caminhos (paths)**. Existem dois tipos:

O **caminho absoluto** começa a partir da raiz `/` e descreve todo o caminho até o arquivo:

```bash
cd /home/usuario/documentos
```

Já o **caminho relativo** depende do diretório atual:

```bash
cd documentos
```

Esses caminhos são fundamentais para navegar no sistema.

O Linux também possui **links**, que funcionam como atalhos para arquivos. Existem dois tipos:

- **Link físico (hard link):** aponta diretamente para o conteúdo do arquivo
- **Link simbólico (soft link):** funciona como um atalho, apontando para o nome do arquivo

Exemplo de link simbólico:

```bash
ln -s arquivo.txt atalho.txt
```

Outro recurso útil é o comando:

```bash
cd -
```

que permite voltar rapidamente para o diretório anterior, pois o sistema "lembra" de onde você estava.

Para buscar arquivos, existem duas ferramentas principais. O comando `locate` faz buscas rápidas em um banco de dados já existente:

```bash
locate arquivo.txt
```

Já o comando `find` realiza uma busca real no sistema de arquivos:

```bash
find /home -name arquivo.txt
```

Ele também pode executar comandos nos arquivos encontrados usando `-exec`:

```bash
find . -name "*.txt" -exec rm {} \;
```

Isso, por exemplo, remove todos os arquivos `.txt` do diretório atual.

O comando `touch` é usado para criar arquivos vazios ou atualizar datas de modificação:

```bash
touch novo.txt
```

Por fim, o Linux utiliza sistemas de gerenciamento de pacotes para instalar e manter programas.

Em sistemas baseados em Debian, usa-se o **apt**:

```bash
sudo apt install programa
```

Em sistemas da família Red Hat, utiliza-se o **dnf**:

```bash
sudo dnf install programa
```

Já no openSUSE, utiliza-se o **zypper**:

```bash
sudo zypper install programa
```

Essas ferramentas permitem instalar, atualizar e remover programas de forma organizada e segura.