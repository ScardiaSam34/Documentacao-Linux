## 13. Usuários, Grupos e Permissões
O Linux é multiusuário desde o design.
Permissões Octais: chmod 755 (Dono: rwx, Grupo: r-x, Outros: r-x).
Sticky Bit: Usado em pastas como /tmp para que apenas o dono de um arquivo possa deletá-lo, mesmo que outros tenham permissão de escrita na pasta.

1. Usuários e Privilégios
O Linux foi projetado para que múltiplas pessoas utilizem o sistema simultaneamente, mantendo a segurança através de diferentes níveis de acesso.

* Identificação: Os comandos who (quem está logado) e whoami (quem sou eu agora) são as ferramentas básicas para verificar a identidade no terminal.

* O Superusuário (Root): Possui controle total e irrestrito. Por segurança, nunca se deve usar a conta root para tarefas diárias.

* O Comando sudo: Permite que usuários comuns executem tarefas administrativas de forma temporária e controlada, sendo a prática recomendada de segurança.

2. O Ambiente Shell (Bash)
Quando você abre um terminal, o shell carrega arquivos de configuração que definem como o sistema se comporta para você.

Arquivos de Inicialização:

* /etc/profile: Configurações globais (afetam todos os usuários).

* ~/.bashrc: Configurações pessoais (específicas para o seu usuário). É aqui que você define atalhos e personaliza o visual do prompt.

* Variáveis de Ambiente: Strings que guardam dados importantes para o sistema (ex: onde encontrar programas ou qual o seu editor de texto padrão).

* Histórico e Atalhos: O comando history permite reutilizar comandos passados, poupando tempo e evitando erros de digitação.

3.Personalização e Produtividade
* O Linux permite que você adapte o sistema ao seu fluxo de trabalho.

* Aliases: São "apelidos" para comandos longos. Por exemplo, você pode criar um alias para que o comando atualizar execute toda a sequência de atualização do sistema.

* Atalhos de Teclado: O Bash oferece atalhos (como Tab para autocompletar ou Ctrl+C para parar um processo) que tornam o uso da linha de comando muito mais veloz.

4. Controle de Acesso (Permissões e Propriedade)
A segurança dos dados no Linux baseia-se em quem é o dono do arquivo e o que ele pode fazer.

* Propriedade:

* chown: Altera o usuário dono do arquivo.

* chgrp: Altera o grupo que tem acesso ao arquivo.

* Permissões (chmod): Define se o dono, o grupo ou outros usuários podem Ler (r), Escrever (w) ou Executar (x) o arquivo.

### Gestão de Usuários e Permissões.

| Comando | O que faz? | Onde aplicar? |
| :--- | :--- | :--- |
| `whoami` | Mostra o usuário atual | Verificação de identidade |
| `sudo` | Eleva privilégios | Instalação de apps / Configuração |
| `chmod` | Muda permissões (rwx) | Proteção de arquivos sensíveis |
| `chown` | Muda o dono do arquivo | Transferência de arquivos entre usuários |
| `alias` | Atalhos personalizados | Otimização de comandos longos |
| `history`| Recupera comandos | Reutilização de tarefas complexas |
