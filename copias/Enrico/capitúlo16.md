## Capitúlo 16

### Lógica Booleana e Operadores
No Shell, quase tudo gira em torno do código de saída (exit code). O valor 0 significa sucesso (verdadeiro) e qualquer outro valor significa erro (falso).
&& (AND): Executa o segundo comando apenas se o primeiro for bem-sucedido.
Ex: mkdir backup && cp arquivo.txt backup/
|| (OR): Executa o segundo comando apenas se o primeiro falhar.
Ex: cd pasta_projeto || echo "Diretório não encontrado"
! (NOT): Inverte o resultado lógico.

### Instrução case vs if-else
Enquanto o if é excelente para comparações lógicas complexas, o case é a escolha ideal para menus ou quando uma única variável pode ter múltiplos valores (como uma estrutura switch-case em Java).
É muito mais legível para tratar argumentos de linha de comando (ex: start, stop, restart).
Permite o uso de wildcards (como *.txt) para capturar padrões.

### Redirecionamento de Saída e Erro (Standard Streams)
Todo comando no Linux lida com três canais:
stdin (0): Entrada (teclado).
stdout (1): Saída padrão (o que deu certo).
stderr (2): Saída de erro (mensagens de falha).
Para depuração, é comum redirecionar ambos para o mesmo lugar:
comando > log.txt 2>&1 (Envia o sucesso e o erro para o arquivo log.txt).

## Depuração (Debugging)
Em vez de tentar adivinhar onde o erro está, você pode executar o script em modo de depuração:
bash -x script.sh: Exibe cada comando e o valor das variáveis antes de executá-los. É como o "step-over" de uma IDE, mas no terminal.

## Arquivos Temporários e Segurança
Usar /tmp é uma prática comum, mas insegura se feita manualmente (risco de colisão de nomes).
O comando mktemp cria um arquivo ou diretório único e aleatório.
Isso garante que dois scripts rodando ao mesmo tempo não sobrescrevam os dados um do outro.

## Geração de Números Aleatórios
Útil para testes de carga, simulações ou criação de nomes de arquivos únicos.
$RANDOM: Uma variável interna do Bash que gera um número entre 0 e 32767.

/dev/urandom: Para necessidades criptográficas mais sérias, lê-se bytes aleatórios diretamente do kernel.