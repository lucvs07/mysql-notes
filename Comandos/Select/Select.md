# Comando SELECT

O comando `SELECT` é usado para consultar e recuperar dados de tabelas no banco de dados. Ele permite selecionar colunas específicas ou todas as colunas de uma tabela.

## Sintaxe Básica

```sql
SELECT coluna1, coluna2, ... 
FROM nome_da_tabela
WHERE condição;
```

- **`coluna1, coluna2, ...`**: As colunas que você deseja recuperar.
- **`nome_da_tabela`**: A tabela de onde os dados serão recuperados.
- **`condição`**: (Opcional) Filtro para especificar quais registros devem ser retornados.

### Exemplos

#### Selecionando Todas as Colunas

```sql
SELECT * 
FROM tabela_1;
```

Este comando retorna todos os registros e todas as colunas da tabela `tabela_1`.

#### Selecionando Colunas Específicas

```sql
SELECT campo1, campo2 
FROM tabela_1;
```

Este comando retorna apenas as colunas `campo1` e `campo2` da tabela `tabela_1`.

#### Usando a Cláusula WHERE

```sql
SELECT * 
FROM tabela_1
WHERE campo2 = '12345';
```

Este comando retorna todos os registros da tabela `tabela_1` onde o valor da coluna `campo2` é igual a `'12345'`.

#### Ordenando os Resultados

```sql
SELECT * 
FROM tabela_1
ORDER BY campo1 ASC;
```

Este comando retorna todos os registros da tabela `tabela_1`, ordenados pela coluna `campo1` em ordem crescente.

#### Limitando o Número de Resultados

```sql
SELECT * 
FROM tabela_1
LIMIT 5;
```

Este comando retorna apenas os primeiros 5 registros da tabela `tabela_1`.

#### Combinando Filtros e Ordenação

```sql
SELECT campo1, campo3 
FROM tabela_1
WHERE campo2 = '12345'
ORDER BY campo1 DESC;
```

Este comando retorna as colunas `campo1` e `campo3` da tabela `tabela_1` para os registros onde `campo2` é igual a `'12345'`, ordenados pela coluna `campo1` em ordem decrescente.
