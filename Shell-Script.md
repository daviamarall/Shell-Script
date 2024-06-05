#### 1. Introdução ao Shell Script

# Curso Básico de Shell Script

## 1. Introdução ao Shell Script

Shell Script é uma linguagem de script usada para automatizar tarefas em sistemas Unix e Unix-like (Linux, macOS). Este curso irá guiá-lo através dos conceitos básicos e avançados de Shell Script, com exemplos práticos.

### O que você aprenderá:
- Estrutura básica de um script
- Variáveis e tipos de dados
- Controle de fluxo e loops
- Funções
- Manipulação de arquivos
- Tratamento de erros e debugging

### Pré-requisitos:
- Acesso a um terminal Unix/Linux
- Conhecimento básico de linha de comando

Vamos começar com o básico!

## 2. Comandos Básicos e Estrutura de um Script

### Estrutura de um Script
Um script básico começa com a linha shebang `#!/bin/bash`, que indica o interpretador a ser usado. 

#### Exemplo: `ola_mundo.sh`
```bash
#!/bin/bash
# Este é o nosso primeiro script
echo "Olá, mundo!"
```

### Executando o Script
1. Torne o script executável:
   ```bash
   chmod +x ola_mundo.sh
   ```
2. Execute o script:
   ```bash
   ./ola_mundo.sh
   ```

### Comandos Básicos
- `echo`: Exibe uma mensagem na tela.
- `ls`: Lista arquivos e diretórios.
- `pwd`: Mostra o diretório atual.
- `cd`: Muda o diretório atual.

#### Exemplo: `comandos_basicos.sh`
```bash
#!/bin/bash
# Listando arquivos no diretório atual
ls
# Mostrando o diretório atual
pwd
```
## 3. Variáveis e Tipos de Dados

### Variáveis
Variáveis armazenam valores temporários que podem ser usados no script.

#### Exemplo: `variaveis.sh`
```bash
#!/bin/bash
# Declarando uma variável
nome="João"
echo "Meu nome é $nome"
```

### Tipos de Dados
- **Strings**: Texto simples.
- **Números**: Inteiros e floats.
- **Arrays**: Listas de valores.

#### Exemplo: `tipos_dados.sh`
```bash
#!/bin/bash
# String
saudacao="Olá"
# Número
idade=25
# Array
frutas=("maçã" "banana" "laranja")

echo $saudacao
echo "Tenho $idade anos"
echo "Minhas frutas favoritas são: ${frutas[@]}"
```

## 4. Estruturas de Controle

### Condicionais
Permitem que você execute comandos com base em condições.

#### Exemplo: `condicional.sh`
```bash
#!/bin/bash
# Condicional if-else
idade=20
if [ $idade -ge 18 ]; then
  echo "Você é maior de idade."
else
  echo "Você é menor de idade."
fi
```

### Case
Permite comparar uma variável com múltiplos valores.

#### Exemplo: `case.sh`
```bash
#!/bin/bash
# Estrutura case
dia="segunda"
case $dia in
  "segunda")
    echo "Hoje é segunda-feira"
    ;;
  "terça")
    echo "Hoje é terça-feira"
    ;;
  *)
    echo "Outro dia"
    ;;
esac
```
```
```
## 5. Loops

### Loop For
Executa comandos para cada item em uma lista.

#### Exemplo: `loop_for.sh`
```bash
#!/bin/bash
# Loop for
for i in {1..5}; do
  echo "Número $i"
done
```

### Loop While
Executa comandos enquanto uma condição é verdadeira.

#### Exemplo: `loop_while.sh`
```bash
#!/bin/bash
# Loop while
contador=1
while [ $contador -le 5 ]; do
  echo "Contador: $contador"
  ((contador++))
done
```
```
```
## 6. Funções

Funções permitem agrupar comandos e reutilizá-los.

### Definindo e Chamando Funções

#### Exemplo: `funcoes.sh`
```bash
#!/bin/bash
# Definindo uma função
minha_funcao() {
  echo "Esta é uma função"
}

# Chamando a função
minha_funcao
```

### Funções com Parâmetros
Funções podem receber parâmetros.

#### Exemplo: `funcao_parametros.sh`
```bash
#!/bin/bash
# Função com parâmetros
saudacao() {
  echo "Olá, $1!"
}

saudacao "Maria"
```
```

## 7. Manipulação de Arquivos

### Criando e Lendo Arquivos
Você pode criar e ler arquivos diretamente no script.

#### Exemplo: `manipulacao_arquivos.sh`
```bash
#!/bin/bash
# Criando um arquivo
echo "Este é um arquivo de teste" > teste.txt

# Lendo um arquivo
cat teste.txt
```

### Verificando a Existência de Arquivos
Verifique se um arquivo ou diretório existe antes de manipulá-lo.

#### Exemplo: `verificacao_arquivo.sh`
```bash
#!/bin/bash
# Verificando se um arquivo existe
if [ -f "teste.txt" ]; then
  echo "O arquivo teste.txt existe."
else
  echo "O arquivo teste.txt não existe."
fi
```
```

## 8. Tratamento de Erros e Debugging

### Tratamento de Erros
Use `set -e` para parar a execução do script se ocorrer um erro.

#### Exemplo: `tratamento_erros.sh`
```bash
#!/bin/bash
set -e
# Comando que irá falhar
cp arquivo_inexistente.txt destino.txt
echo "Este comando não será executado devido ao erro anterior."
```

### Debugging
Use `set -x` para ativar o modo de depuração e ver os comandos enquanto são executados.

#### Exemplo: `debugging.sh`
```bash
#!/bin/bash
set -x
# Comandos para depuração
echo "Depuração ativada"
ls
set +x
echo "Depuração desativada"
```


## 9. Exercícios Práticos

### Exercício 1: Script de Backup
Crie um script que faça backup de um diretório especificado para um diretório de backup.

#### Exemplo: `backup.sh`

```bash
#!/bin/bash
# Diretório de origem
origem="/caminho/para/origem"
# Diretório de destino
destino="/caminho/para/backup"
# Nome do arquivo de backup
arquivo_backup="backup_$(date +%Y%m%d%H%M%S).tar.gz"

# Criando o backup
tar -czf $destino/$arquivo_backup $origem
echo "Backup criado em $destino/$arquivo_backup"
```

### Exercício 2: Verificação de Utilização de Disco
Crie um script que verifique a utilização do disco e envie um alerta se a utilização ultrapassar um determinado limite.

#### Exemplo: `verificacao_disco.sh`
```bash
#!/bin/bash
# Limite de utilização em porcentagem
limite=80
# Verificando a utilização do disco
utilizacao=$(df / | grep / | awk '{ print $5 }' | sed 's/%//g')

if [ $utilizacao -ge $limite ]; then
  echo "Alerta: Utilização do disco é de $utilizacao%!"
else
  echo "Utilização do disco está dentro do limite."
fi
```
```
