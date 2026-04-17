### 09. Documentação auxiliar Linux

O man é a referência clássica e offline. Quase todo comando ou arquivo de configuração instalado possui uma página de manual associada.

Estrutura por Seções: As páginas são divididas em seções para evitar confusão entre comandos e arquivos com nomes iguais:

1: Comandos de usuário (ex: ls, mkdir).
5: Formatos de arquivos de configuração (ex: /etc/passwd).
8: Comandos de administração do sistema (ex: iptables).

 Seções do Man: man 1 (comandos de usuário), man 5 (formatos de arquivos como o /etc/passwd), man 8 (comandos de administração).

 Comandos Úteis:

* man <comando>: Abre o manual.

* man -k <termo>: (Apropos) Pesquisa manuais que contenham uma palavra-chave específica.

* man 5 passwd: Abre especificamente o manual sobre o formato do arquivo de senhas, ignorando o comando de trocar senha.

### GNU Info System (info)
Enquanto o man foca em páginas únicas e técnicas, o info é projetado para ser um manual hipertextual (como um site antigo dentro do terminal).

Vantagem: Oferece uma leitura mais fluida e organizada em "nós" (nodes). É onde reside a documentação completa de ferramentas do projeto GNU (como o compilador GCC ou o shell Bash).

Navegação: Diferente do man (que usa apenas scroll), o info permite saltar entre links, avançar capítulos e retornar ao índice principal.

### Ajuda Rápida (--help e help)
Ideal para quando você esqueceu apenas a sintaxe de uma opção específica e não quer ler um manual inteiro.

Argumentos -h ou --help: São padrões da maioria dos programas. Eles imprimem uma lista rápida de opções diretamente na tela de saída.

Comando help (Built-ins): No shell Bash, o comando help é usado para comandos que não são programas independentes, mas sim funções internas do próprio shell (como cd, alias ou export).

Nota: Tentar man cd pode não funcionar em algumas distros; nesses casos, use help cd.

Guia de Referência: Ajuda e Documentação no Linux

| Comando | Função Principal | Exemplo de Uso |
| :--- | :--- | :--- |
| `man <comando>` | Abre o manual completo (offline) do comando. | `man grep` |
| `man -k <termo>` | Busca comandos relacionados a uma palavra-chave. | `man -k user` |
| `man <seção> <item>` | Acessa uma seção específica (ex: 5 para configurações). | `man 5 shadow` |
| `info <comando>` | Documentação em formato de nós (estilo hipertexto). | `info coreutils` |
| `<comando> --help` | Exibe resumo de sintaxe e opções no terminal. | `ls --help` |
| `help <comando>` | Ajuda para comandos internos do Shell (Built-ins). | `help alias` |
| `whatis <comando>` | Descrição rápida (uma linha) sobre o que o comando faz. | `whatis chmod` |
| `apropos <termo>` | Lista comandos que realizam determinada função. | `apropos search` |
| `whereis <comando>` | Localiza o binário, manual e fontes de um programa. | `whereis bash` |
| `type <comando>` | Revela se o comando é binário, alias ou função interna. | `type ll` |

---
