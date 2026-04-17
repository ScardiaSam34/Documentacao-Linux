## O Poder do Superusuário (Root)
No Linux, o usuário root é onipotente. Ele ignora todas as permissões de arquivos e restrições do sistema.

Necessidade: Você precisa de privilégios de root para instalar softwares, reiniciar serviços do sistema e alterar arquivos de configuração globais.

Ferramentas de Acesso:

su (substitute user): Muda completamente para outra identidade (geralmente root).

sudo (superuser do): Executa um comando específico com poderes de administrador sem precisar sair da sua conta atual.

## O Guardião: /etc/sudoers
O comando sudo não é liberado para todos. Ele consulta o arquivo de configuração /etc/sudoers para verificar:

Se o usuário tem permissão para usar o sudo.

Quais comandos específicos ele pode executar.

Se ele precisa digitar a própria senha para validar a ação.
## Auditoria e Logs
Uma das funções mais críticas em ambientes corporativos (como na 2RP) é o rastreio. O sudo registra todas as tentativas de uso, especialmente as falhas.

Debian/Ubuntu: Os registros ficam em /var/log/auth.log.

Outras distros: Geralmente em /var/log/messages ou /var/log/secure.
## Autenticação e Criptografia de Senhas
O Linux não "sabe" sua senha; ele sabe o hash dela.

SHA-512: É o algoritmo padrão atual. Ele transforma sua senha em uma sequência longa e única.

Unidirecional: O sistema pode criptografar sua senha para comparar com o que está guardado, mas não consegue descriptografar o hash para ler a senha original.

PAM (Pluggable Authentication Modules): É uma camada flexível que permite ao administrador definir regras de complexidade (ex: exigir letras maiúsculas, números e símbolos).

## Segurança de Processos e Física
Isolamento: Por segurança, um processo não pode "espiar" ou acessar recursos de outro, mesmo que ambos pertençam ao mesmo usuário.

Acesso Físico: A segurança digital de nada vale se alguém puder tocar fisicamente no servidor (lembra da importância da senha na BIOS que vimos anteriormente?).

Atualizações: Manter o sistema atualizado é o método mais eficaz para fechar vulnerabilidades conhecidas.