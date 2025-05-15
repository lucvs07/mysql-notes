# Aula 05 - FUNÇÕES

## String

```sql
SELECT NOME, CONCAT(ENDERECO_1, ' ', BAIRRO, ' ', CIDADE, ' ', ESTADO) AS 'ENDEREÇO'
FROM tabela_de_clientes;
```

## Datas

```sql
SELECT NOME, (YEAR(current_date()) - YEAR(DATA_DE_NASCIMENTO)) AS 'IDADE'
FROM tabela_de_clientes
ORDER BY IDADE ASC;

SELECT NOME, timestampdiff(YEAR, DATA_DE_NASCIMENTO, CURRENT_DATE()) AS 'IDADE'
FROM tabela_de_clientes
ORDER BY IDADE ASC;

```

## Matemáticas

```sql
SELECT YEAR(DATA_VENDA) AS ANO, FLOOR(SUM(IMPOSTO * (QUANTIDADE * PRECO))) AS IMPOSTO
FROM notas_fiscais NF
INNER JOIN itens_notas_fiscais INF ON NF.NUMERO = INF.NUMERO
WHERE YEAR(DATA_VENDA) = 2016
GROUP BY ANO;

```

## Conversão de Dados

```sql
SELECT CONCAT('O dia de hoje é: ',
DATE_FORMAT(current_timestamp(), '%d/%c/%y')
) as Resultado

SELECT CONVERT(40.444, CHAR) AS RESULTADO;

```
