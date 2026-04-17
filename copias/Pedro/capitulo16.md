# Mais sobre operações e programação no shell

## 1. Manipulação de Strings
No Shell, strings podem ser manipuladas diretamente para comparações ou processadas por ferramentas externas para ordenação.

### Comparação
Utilize os colchetes duplos `[[ ]]` para testar igualdade ou padrões.
* `[[ $a == $b ]]` : Igualdade.
* `[[ $a != $b ]]` : Diferença.
* `[[ $a =~ ^[0-9]+$ ]]` : Validação por Expressão Regular (ex: se é número).

### Ordenação
A ordenação de listas dentro de variáveis requer o comando `sort`.
```bash
LISTA_FRUTAS="Uva\nAbacate\nMelancia\nBanana"
echo -e "$LISTA_FRUTAS" | sort 
```
___

## 2. Expressões booleanas e tipos de dados

O Shell avalia condições de forma distinta para textos, números e arquivos.

| Categoria | Operador | Descrição |
| :--- | :--- | :--- |
| **String** | `-z "$str"` | Verdadeiro se a string for vazia. |
| **Números** | `-eq`, `-ne` | Igual e Diferente (Equal / Not Equal). |
| **Números** | `-gt`, `-lt` | Maior e Menor que (Greater / Less than). |
| **Arquivos** | `-e "$arq"` | Verifica se o arquivo/diretório existe. |
| **Arquivos** | `-d "$arq"` | Verifica se é especificamente um diretório. |

### Exemplo prático
``` Bash
# Verifica se o arquivo existe E se o tamanho é maior que zero
if [[ -s "logs.txt" && "$USUARIO" == "admin" ]]; then
    echo "O log não está vazio e o usuário é admin."
fi
```

## 3. Uso de `case` para parâmetros

A declaração `case` substitui múltiplos `if/else` ao lidar com argumentos passados via linha de comando ($1, $2, etc.).

```bash
case "$1" in
    -a|--add)
        echo "Adicionando novo usuário..."
        ;;
    -d|--del)
        echo "Removendo usuário..."
        ;;
    *)
        echo "Opção inválida. Use --add ou --del."
        exit 1
        ;;
esac
```

---

## 4. Construtos de looping
Os loops facilitam a execução repetitiva de tarefas.

### For Loop
Ideal para iterar sobre sequências ou arquivos.
```bash
for i in {1..5}; do
    echo "Contagem: $i"
done
```

### While Loop
Executa enquanto a condição for verdadeira.
```bash
while [ ! -f "finalizar.txt" ]; do
    echo "Aguardando arquivo de sinalização..."
    sleep 2
done
```

## 5. Debugging com `set -x` e `set +x`
Para encontrar erros, use o comando `set -x` para imprimir cada comando antes de executá-lo (modo Verbose).

```bash
set -x # Liga o debug
VAR_TESTE="Shell"
[[ $VAR_TESTE == "Linux" ]]
set +x # Desliga o debug
```

## 6. Arquivos e Diretórios Temporários
O comando `mktemp` garante que você crie arquivos ou pastas com nomes únicos, evitando que scripts diferentes sobrescrevam dados uns dos outros.
```bash
# Cria arquivo temporário
MEU_ARQUIVO=$(mktemp) 

# Cria diretório temporário
MEU_DIR=$(mktemp -d)

echo "Arquivo criado em: $MEU_ARQUIVO"

# Boa prática: Remover ao sair do script
trap "rm -f $MEU_ARQUIVO; rm -rf $MEU_DIR" EXIT
```

## 7. Números Aleatórios
A variável interna `$RANDOM` gera um número entre 0 e 32767. Para obter um intervalo específico, usamos o operador de módulo `%`.
```bash
# Número aleatório entre 0 e 10
NUMERO=$(( RANDOM % 11 ))

# Número aleatório entre 50 e 100
FAIXA=$(( (RANDOM % 51) + 50 ))

echo "O número sorteado foi: $FAIXA"
```