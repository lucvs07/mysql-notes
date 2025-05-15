# SCRIPTS AULA 04 - JOIN & UNION

## INNER JOIN

```sql
SELECT * FROM tabela_de_vendedores V
INNER JOIN notas_fiscais F
ON V.MATRICULA = F.MATRICULA;

SELECT V.MATRICULA, V.NOME, COUNT(*) AS QTD
FROM tabela_de_vendedores V
INNER JOIN notas_fiscais F
ON V.MATRICULA = F.MATRICULA
GROUP BY V.MATRICULA, V.NOME;

SELECT YEAR(DATA_VENDA) AS ANO, SUM(QUANTIDADE * PRECO) AS FATURAMENTO
FROM notas_fiscais F INNER JOIN itens_notas_fiscais INF
ON F.NUMERO = INF.NUMERO
GROUP BY ANO
ORDER BY FATURAMENTO DESC;

SELECT tabela_de_vendedores.BAIRRO as 'Bairro Vendedor',
tabela_de_vendedores.NOME as 'Vendedor',
DE_FERIAS,
tabela_de_clientes.BAIRRO as 'Bairro Cliente',
tabela_de_clientes.NOME as 'Cliente' FROM tabela_de_vendedores INNER JOIN tabela_de_clientes
ON tabela_de_vendedores.BAIRRO = tabela_de_clientes.BAIRRO;
```

## LEFT JOIN

```sql
SELECT DISTINCT A.CPF, A.NOME, B.CPF FROM tabela_de_clientes A
LEFT JOIN notas_fiscais B ON A.CPF = B.CPF;

SELECT DISTINCT A.CPF, A.NOME, B.CPF FROM tabela_de_clientes A
LEFT JOIN notas_fiscais B ON A.CPF = B.CPF
WHERE B.CPF IS NULL;

SELECT DISTINCT A.CPF, A.NOME, B.CPF FROM tabela_de_clientes A
LEFT JOIN notas_fiscais B ON A.CPF = B.CPF
WHERE B.CPF IS NULL AND YEAR(B.DATA_VENDA) = 2015;

SELECT tabela_de_vendedores.BAIRRO as 'Bairro Vendedor',
tabela_de_vendedores.NOME as 'Vendedor',
DE_FERIAS,
tabela_de_clientes.BAIRRO as 'Bairro Cliente',
tabela_de_clientes.NOME as 'Cliente' FROM tabela_de_vendedores LEFT JOIN tabela_de_clientes
ON tabela_de_vendedores.BAIRRO = tabela_de_clientes.BAIRRO;
```

## RIGHT JOIN

```sql
SELECT DISTINCT A.CPF, A.NOME, B.CPF FROM notas_fiscais B
RIGHT JOIN tabela_de_clientes A ON A.CPF = B.CPF;

SELECT tabela_de_vendedores.BAIRRO as 'Bairro Vendedor',
tabela_de_vendedores.NOME as 'Vendedor',
DE_FERIAS,
tabela_de_clientes.BAIRRO as 'Bairro Cliente',
tabela_de_clientes.NOME as 'Cliente' FROM tabela_de_vendedores RIGHT JOIN tabela_de_clientes
ON tabela_de_vendedores.BAIRRO = tabela_de_clientes.BAIRRO;
```

## FULL e CROSS JOIN

```sql

-- CROSS JOIN
SELECT tabela_de_vendedores.BAIRRO as 'Bairro Vendedor',
tabela_de_vendedores.NOME as 'Vendedor',
DE_FERIAS,
tabela_de_clientes.BAIRRO as 'Bairro Cliente',
tabela_de_clientes.NOME as 'Cliente' FROM tabela_de_vendedores, tabela_de_clientes;
```

## UNION

**Explicação:**

- O comando `UNION` é usado para combinar os resultados de múltiplas consultas SELECT em um único conjunto de resultados.
- As colunas das consultas devem ter o mesmo número e tipo de dados.
- `UNION` remove duplicatas automaticamente, enquanto `UNION ALL` mantém todas as linhas, incluindo duplicatas.
- Pode ser útil para consolidar dados de tabelas diferentes com estrutura semelhante.

```sql
-- UNION combina os resultados de duas ou mais consultas SELECT.
-- Ele remove duplicatas por padrão, a menos que UNION ALL seja usado.

-- Exemplo 1: UNION simples
SELECT NOME, CPF FROM tabela_de_clientes
UNION
SELECT NOME, CPF FROM tabela_de_vendedores;

-- Exemplo 2: UNION ALL (mantém duplicatas)
SELECT NOME, CPF FROM tabela_de_clientes
UNION ALL
SELECT NOME, CPF FROM tabela_de_vendedores;

-- Exemplo 3: UNION com filtros diferentes
SELECT NOME, CPF FROM tabela_de_clientes WHERE BAIRRO = 'Brás'
UNION
SELECT NOME, CPF FROM tabela_de_vendedores WHERE DE_FERIAS = 1;
```

## SUBCONSULTAS

- Utiliza-se dentro de uma consulta principal

```sql
SELECT X,Y FROM tab1 
WHERE Y IN (SELECT Y from tab2)

SELECT * FROM tabela_de_clientes
WHERE BAIRRO IN (
SELECT DISTINCT BAIRRO from tabela_de_vendedores
);

```

## VISÃO (VIEW)

- É uma `tabela lógica` -> resultado de uma consulta

```sql
CREATE VIEW 'VW_MAIORES_EMBALAGENS' AS
SELECT EMBALAGEM, MAX(PRECO_DE_LISTA) AS MAIOR_PRECO FROM tabela_de_produtos
GROUP BY EMBALAGEM
```
