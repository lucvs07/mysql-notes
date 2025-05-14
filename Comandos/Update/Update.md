# Comando UPDATE no SQL

O comando `UPDATE` no SQL é usado para modificar os dados existentes em uma tabela. Ele permite alterar valores em uma ou mais colunas de uma ou mais linhas, com base em condições especificadas.

## Estrutura básica do comando

```sql
UPDATE nome_da_tabela
SET coluna1 = valor1, coluna2 = valor2, ...
WHERE condição;
```

## Exemplos e explicações

### 1. Atualizar uma única coluna

```sql
UPDATE clientes
SET cidade = 'São Paulo'
WHERE id = 1;
```

Neste exemplo, a coluna `cidade` da tabela `clientes` será atualizada para `São Paulo` apenas para a linha onde o `id` é igual a 1.

### 2. Atualizar múltiplas colunas

```sql
UPDATE produtos
SET preco = 19.99, estoque = 50
WHERE categoria = 'Eletrônicos';
```

Aqui, as colunas `preco` e `estoque` da tabela `produtos` serão atualizadas para `19.99` e `50`, respectivamente, para todas as linhas onde a `categoria` é `Eletrônicos`.

### 3. Atualizar todas as linhas (cuidado ao omitir a cláusula WHERE)

```sql
UPDATE funcionarios
SET salario = salario * 1.1;
```

Este comando aumenta o salário de todos os funcionários em 10%, pois não há uma condição especificada.

## Observações importantes

- Sempre use a cláusula `WHERE` para evitar alterações indesejadas em todas as linhas da tabela.
- Faça backup dos dados antes de executar comandos `UPDATE` em tabelas críticas.
- Teste o comando em um ambiente de desenvolvimento antes de aplicá-lo em produção.
