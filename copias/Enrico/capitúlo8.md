## Capítulo 08.
    O Linux oferece múltiplas formas de interação, desde o hardware físico até ambientes virtuais:

Terminais Virtuais (VT): São consoles de linha de comando que utilizam diretamente o monitor e o teclado do sistema.

Emuladores de Terminal: Funcionam dentro de janelas em ambientes gráficos (como GNOME ou KDE), simulando o comportamento de um terminal físico.

Acesso e Login: É possível logar localmente via terminal de texto ou remotamente. Por segurança, ao digitar senhas, nenhum caractere ou símbolo é exibido.

Gerenciamento de Sessão: O comando shutdown é o método preferencial e seguro para desligar ou reiniciar o sistema, garantindo a integridade dos dados.

Sistema de Arquivos e Navegação
A organização de arquivos no Linux segue uma estrutura hierárquica bem definida:

Tipos de Caminhos
Absoluto: Começa sempre na raiz (/) e descreve todo o caminho até o destino.

Relativo: Começa a partir do diretório onde você está no momento (diretório de trabalho).

Atalhos e Links
Links: O sistema utiliza links físicos (apontam para os dados no disco) e links simbólicos/soft links (atalhos para outros arquivos).

Navegação Rápida: O comando cd - funciona como um botão "voltar", retornando o usuário ao diretório anterior.
Busca e Manipulação de Arquivos
Existem ferramentas específicas para encontrar e modificar arquivos de forma eficiente:

* locate: Busca rápida baseada em um banco de dados pré-indexado de nomes de arquivos.

* find: Ferramenta poderosa que busca arquivos em tempo real. Com a opção -exec, permite executar comandos diretamente nos resultados encontrados.

* touch: Utilizado para criar arquivos vazios ou atualizar as datas de acesso e modificação de arquivos existentes.

### Gerenciamento de Pacotes
Cada "família" de distribuições Linux possui sua própria ferramenta para instalar e atualizar softwares:

| Gerenciador | Distribuição Base | Formato |
| :--- | :--- | :--- |
| **APT** | Debian, Ubuntu, Linux Mint | `.deb` |
| **DNF** | Red Hat, Fedora, CentOS | `.rpm` |
| **Zypper** | openSUSE | `.rpm` |