# Capítulo 11 — Editores de Texto no Linux

## Nano: simples e direto

Dentro do nano, você já pode começar a digitar normalmente. Os comandos aparecem na tela, como:

```bash
Ctrl + O → salvar
Ctrl + X → sair
```

Isso torna o nano ideal para iniciantes ou para edições rápidas.

---

## Gedit: editor gráfico

O gedit é um editor com interface gráfica, parecido com o Bloco de Notas do Windows, mas mais completo. Ele é usado em ambientes com interface gráfica (como GNOME).

Para abrir:

```bash
gedit arquivo.txt
```

Ele permite abrir múltiplos arquivos, usar abas, destacar código (syntax highlighting) e configurar preferências. É mais confortável para quem prefere interface visual.

---

## Vi (ou Vim): poderoso e universal

O vi (ou sua versão mais moderna, o vim) é um dos editores mais importantes do Linux. Ele está presente praticamente em todos os sistemas, inclusive servidores onde não existe interface gráfica.

Para abrir:

```bash
vi arquivo.txt
```

O diferencial do vi é que ele trabalha com modos, e isso pode confundir no começo:

- **Modo comando (Command Mode):** é o padrão ao abrir o editor. Aqui, as teclas executam ações (não escrevem texto).
- **Modo inserção (Insert Mode):** permite digitar texto normalmente (ativado com `i`).
- **Modo linha (Line Mode):** usado para comandos como salvar e sair (ativado com `:`).

### Exemplo básico:

```bash
i  -> entra no modo inserção
digite o texto
Esc -> volta para modo comando
:wq -> salva e sai
```

---

## Vimtutor: aprendendo na prática

O Linux oferece um tutorial interativo para aprender o vi:

```bash
vimtutor
```

Ele ensina passo a passo os comandos básicos, sendo uma das melhores formas de aprender esse editor.

---

## Emacs: alternativa poderosa

O Emacs é outro editor extremamente poderoso e muito utilizado. Diferente do vi, ele não usa modos da mesma forma, mas depende de combinações de teclas com Ctrl e Alt.

Para abrir:

```bash
emacs arquivo.txt
```

Para acessar o tutorial dentro dele:

```bash
Ctrl + h
t
```

O Emacs pode ser usado tanto no terminal quanto com interface gráfica e é altamente personalizável, podendo até funcionar como ambiente completo de desenvolvimento.

---

## Diferenças e uso na prática

Tanto o vi quanto o Emacs são ferramentas muito completas, mas possuem estilos diferentes:

- O vi/vim é mais leve e sempre disponível
- O Emacs é mais expansível e configurável
- O nano é simples e ideal para iniciantes
- O gedit é melhor para uso gráfico

No início, pode parecer difícil usar editores como vi ou Emacs, principalmente por causa das teclas e comandos. Porém, depois de aprender, eles se tornam extremamente rápidos e eficientes.

---

## Exemplo prático

Editar um arquivo de configuração:

```bash
sudo nano /etc/hosts
```

Ou com vi:

```bash
sudo vi /etc/hosts
```

Isso permite modificar configurações do sistema diretamente.
