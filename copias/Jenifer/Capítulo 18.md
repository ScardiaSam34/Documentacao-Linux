# Capítulo 18 — Segurança, Usuários e Privilégios no Linux

No Linux, a segurança do sistema gira principalmente em torno do controle de usuários e permissões. O elemento central disso é a conta **root**, que é o administrador do sistema. Esse usuário tem acesso total a tudo: pode modificar arquivos críticos, instalar programas, alterar configurações e até apagar o sistema inteiro. Por isso, o uso direto do root deve ser evitado sempre que possível.

Em vez de usar o root diretamente, o Linux oferece formas mais seguras de executar tarefas administrativas. As principais são os comandos `su` e `sudo`. O `su` permite trocar para outro usuário (geralmente o root), assumindo completamente aquele ambiente. Já o `sudo` é mais seguro, pois permite executar apenas um comando com privilégios elevados, sem precisar mudar de usuário permanentemente.

Exemplo:

```bash
sudo apt update
```

Nesse caso, o comando é executado com permissões de administrador, mas o restante da sessão continua como usuário comum.

O uso do `sudo` é controlado por arquivos como `/etc/sudoers` e `/etc/sudoers.d`, onde são definidas regras sobre quem pode executar quais comandos. Isso permite um controle muito mais detalhado e seguro. Além disso, todas as tentativas de uso do `sudo`, inclusive falhas, são registradas em logs do sistema (como `/var/log/auth.log`), o que ajuda na auditoria e na detecção de problemas de segurança.

---

Outro ponto importante é o **isolamento de processos**. No Linux, um processo não pode acessar diretamente os recursos de outro, mesmo que ambos pertençam ao mesmo usuário. Isso aumenta a segurança, evitando que um programa com erro ou malicioso afete outros.

O sistema também utiliza **credenciais de usuário** para verificar identidade e permissões. Sempre que você executa algo, o sistema verifica quem você é e o que você tem permissão para fazer.

---

As **senhas** são protegidas por criptografia forte, geralmente usando o algoritmo **SHA-512**. Isso significa que a senha não é armazenada de forma legível, mas sim como um valor criptografado. Mesmo que alguém tenha acesso ao arquivo de senhas, não conseguirá ver a senha original.

Além disso, o Linux pode usar o sistema **PAM (Pluggable Authentication Modules)** para reforçar a segurança. Com ele, é possível definir regras como:

- exigir senhas fortes
- bloquear tentativas repetidas de login
- aplicar políticas de segurança personalizadas

Por exemplo, ao alterar uma senha com `passwd`, o sistema pode exigir que ela tenha letras, números e caracteres especiais.

---

A segurança no Linux não depende apenas do software. O **acesso físico** ao computador também é um fator crítico. Se alguém tiver acesso direto à máquina, pode tentar invadir o sistema usando dispositivos externos ou outras técnicas. Por isso, é importante:

- proteger BIOS/UEFI com senha
- evitar boot por dispositivos externos
- restringir acesso físico ao equipamento

---

Outro ponto essencial é manter o sistema sempre **atualizado**. Atualizações corrigem falhas de segurança que podem ser exploradas por atacantes.

Exemplo:

```bash
sudo apt update && sudo apt upgrade
```

Isso garante que o sistema esteja protegido contra vulnerabilidades conhecidas.

