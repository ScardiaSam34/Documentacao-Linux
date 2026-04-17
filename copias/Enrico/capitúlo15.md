## Capitúlo 15
Neste capitúlo veremos algumas caracteristicas dos shell e script bash, utilizaremos instruções condicionais como blocos if-then-else e realizaremos operações aritméticas usando linguagem de script.

O que é um Shell Script?
É essencialmente um arquivo de texto contendo uma sequência de comandos que o sistema operacional deve executar. No Linux, o interpretador padrão é o Bash (Bourne Again Shell).

Lógica de Execução
Para o seu exemplo de verificar um arquivo, o script segue uma lógica condicional simples:

Entrada: Recebe o nome do arquivo.

Processamento: O shell testa se o caminho existe (usando operadores como -e ou -f).

Saída: Exibe uma mensagem de confirmação ("Arquivo encontrado") ou de erro ("Arquivo não existe").

Benefícios da Automação
O texto e o gráfico mencionam que a automação é superior à execução manual por diversos motivos:

Economia de Tempo: Comandos complexos são executados instantaneamente com um único chamado do script.

Consistência: O script sempre executará os comandos na mesma ordem e com as mesmas regras, eliminando o erro humano de digitação.

Repetibilidade: Uma vez escrito, o script pode ser usado milhares de vezes ou agendado para rodar sozinho (como via cron).

Portabilidade: Você pode levar seu script para diferentes servidores e manter o mesmo padrão de trabalho.

O Linux oferece uma ampla variedade de shells; as opções disponíveis no sistema estão listadas em /etc/shells . Algumas opções típicas são:

/bin/sh
/bin/bash
/bin/tcsh
/bin/csh
/bin/ksh
/bin/zsh

## Sintaxe básica e caracteres especiais:
Os scripts exigem que você siga uma sintaxe de linguagem padrão. Regras definem como definir variáveis ​​e como construir e formatar instruções permitidas, etc. A tabela lista alguns usos de caracteres especiais em scripts bash:

### Caracteres Especiais no Shell Bash

| Personagem | Descrição |
| :---: | :--- |
| **#** | Usado para adicionar um comentário, exceto quando usado como `\#` ou como `#!` ao iniciar um script. |
| **\\** | Usado no final de uma linha para indicar a continuação para a linha seguinte ou para indicar que o próximo caractere deve ser interpretado literalmente. |
| **;** | Utilizado para interpretar o que se segue como um novo comando a ser executado após a conclusão do comando atual. |
| **$** | Indica que o que se segue é uma variável (como variáveis de ambiente ou do sistema). |
| **>** | Redirecionar saída (sobrescreve o conteúdo do destino). |
| **>>** | Anexar saída (adiciona ao final do conteúdo existente sem apagar). |
| **<** | Redirecionar entrada. |
| **\|** | **Pipe:** Utilizado para direcionar o resultado (saída) de um comando para a entrada do próximo comando. |

Existem outros caracteres especiais, combinações de caracteres e construções que os scripts entendem, como (..) , {..} , [..] , && , || , ' , " , $((...)) , alguns dos quais discutiremos mais tarde.

