# Linhas de comando 
*"A interface gráfica faz tarefas fáceis ficarem ainda mais fáceis, enquanto as linhas de comando fazem tarefas difíceis possíveis"*

## Características 
- Toda e qualquer tarefa pode ser realizada através das linhas de comando
- É possível fazer scripts para automatizar comandos muito utilizados ou facilmente esquecíveis ou também para uma série de processos
- Pode iniciar aplicações gráficas através de linhas de comando, ao invés de navegar entre diferentes menus e janelas
- As linhas de comando também são padronizadas, até mesmo em diferentes distros

##  Elementos dos comandos
- Comando inserido
- Opções (flags): começam com - ou -- para poderem ser diferenciadas dos argumentos 
- Argumentos

## Links 🔗
### Hard links
São arquivos independentes que dividem a mesma partição de outro arquivo dentro do msm disco.

**Cuidado durante seu uso!!**

- Se você excluir um dos arquivos, o outro ainda existirá dentro daquela mesma partição
- Se você editar um dos dois arquivos, o link pode ser quebrado ou os arquivos podem se sobreescreverem

### Soft links
Diferentemente dos hard links, não ocupam espaço dentro da memória. Na verdade, eles funcionam basicamente como atalhos para um outro arquivo (assim como os atalhos da área de trabalho do Windows, por exemplo)

## Fluxo padrão de arquivos 
- stdin (standard input) -> entrada.
- stdout (standard output) -> saída.
- stderr (standard errors) -> erros.

## Redirecionamento de E/S (entrada/saída)
Através do shell de comando, você pode usar símbolos de > e < para indicar um novo arquivo para ser considerado como entrada e/ou saída
- **>:** Redireciona a saída para um arquivo, salvando o resultado da saída dentro desse mesmo arquivo
- **<:** Redireciona a entrada para um arquivo, usando esse arquivo como entrada ou como elemento dentro de um comando
- **2>:** Redireciona o erro para um arquivo, salvando o resultado do erro dentro desse mesmo arquivo
-**2>&1** ou **>&:** Redireciona todas as entradas e saídas para o mesmo arquivo

## Caracteres coringas
- **?:** substitui qualquer caractere (um único caractere)
- __*__: substitui qualquer palavra/string
- **[conjunto]:** procura por qualquer letra que esteja dentro desse conjunto
- **[!conjunto]:** procura por qualquer letra que não esteja dentro desse conjunto

## Operações e comandos
- **cd:** mostra o último repositório acessado
- **cd ~ :** volta para o diretório home 
- **cd.. :** muda para o diretório pai
- **cd- :** volta ao último repositório acessado
- **cd/ :** muda para o diretório root
___
- **cat :** usado para criar, concatenar e visualizar arquivos
- **echo :** usado para manipulação de texto e formatação de saída
___
- **ls :** lista o conteúdo do diretório atual
- **ls -a :** lista todo o conteúdo do diretório atual, incluindo arquivos ocultos
___
- **rmdir :** deleta um diretório vazio
- **man :** acessa um manual de funções, programas e comandos do sistema
- **exit :** sai da sessão atual do shell
- **login :** inicia um novo login do shell
___
- **mkdir :** cria um novo diretório
- **mkdir /caminho/indicado :** cria um repositório no caminho indicado
___
- **which :** usado para identificar a localização de um programa
- **whereis :** usado para identificar a localização dum programa, junto de suas dependências e repositórios pais
- **pwd :** mostra o repositório pai
- **tree :** mostra a árvore de repositórios até o arquivo atual
___
- **ln :** cria um hard link
- **ln -s :** cria um soft link
___
- **pushd :** muda de repositório
- **popd :** começa a fazer o caminho contrário da sua stack de repositórios
- **dirs :** visualiza sua stack pela ordem de acessos
- **tac :** usado para visualizar arquivos de modo contrário
- **less :** usado para ver arquivos de forma paginada
- **tail n :** usado para ver as últimas 'n' linhas de um arquivo
- **head n :** usado para ver as primeiras 'n' linhas de um arquivo
___
- **touch nomearquivo :** cria um novo arquivo vazio
- **touch -a nomearquivo :** altera o timestamp do arquivo para o momento atual
- **touch -r arquivoReferencia arquivoDestino :** clona os dados do arquivo de referência para um arquivo de destino
- **touch nomearquivo{1..3} :** cria múltiplos arquivos
____
- **mv :** renomeia e/ou move um arquivo
- **mv nomearquivoAntes nomearquivoDepois :** renomeia um arquivo
- **mv nomearquivo /caminho/desejado :** move um arquivo para o caminho desejado
___  
- **rm :** remove um arquivo
- **rm -rf :** deleta um diretório ou arquivo e todos os seus conteúdos
- **rm -f :** remove um arquivo de modo forçado
- **rm -i :** remove um arquivo ou diretório de modo interativo
___
- **locate :** procura quaisquer entradas que combinem com sua busca, para seu melhor funcionamento é bom utilizar de pipes (|)
- **locate zip | grep bin :** vai procurar arquivos que possuam zip e bin
___
- **find :** lista todos os arquivos no diretório atual e todos seus subdiretórios
- **find -name :** lista apenas os arquivos com determinado padrão em seus nomes
- **find -iname :** lista apenas os arquivos com determinado padrão em seus nomes, mas ignorando letras minúsculas e maiúsculas
- **find -d :** restringe os resultados apenas a diretórios
- **find -f :** restringe os resultados apenas a arquivos comuns
- **find -l :** restringe os resultados apenas a soft links
___