# Aula 03

## DISTINCT

- Irá retornar somente linhas com valores diferentes

```sql
SELECT DISTINCT * FROM TABELA;
```

## LIMIT

- Irá LIMITAR a quantidade de dados exibidos

```sql
SELECT * FROM TABELA LIMIT quantidade;

SELECT * FROM TABELA LIMIT 2,3
-- A partir do segundo elemento, irei buscar os 3 seguintes
```

## ORDER BY

- Apresenta o resultado da consulta ordenado pelo campo determinado

- É posível ter mais de um campo determinado para a ordenação

```sql
SELECT * FROM TABELA ORDER BY coluna ASC;
-- Ordena os resultados pela coluna em ordem crescente

SELECT * FROM TABELA ORDER BY coluna DESC;
-- Ordena os resultados pela coluna em ordem decrescente
```

## GROUP BY

- Agrupa os resultados da consulta com base em um ou mais campos especificados.

- Geralmente usado com funções de agregação como `SUM`, `COUNT`, `AVG`, `MAX` e `MIN`.

```sql
SELECT coluna, COUNT(*)
FROM TABELA
GROUP BY coluna;
-- Agrupa os dados pela coluna especificada e conta a quantidade de registros em cada grupo
```

```sql
SELECT coluna, SUM(valor)
FROM TABELA
GROUP BY coluna;
-- Agrupa os dados pela coluna especificada e calcula a soma dos valores em cada grupo
```

### Having

- É uma condição (`Filtro`) que se aplica ao resultado de uma agregaçãp (`group by`)

```sql
SELECT coluna, COUNT(*)
FROM TABELA
GROUP BY coluna
HAVING COUNT(*) > 1;
-- Filtra os grupos onde a contagem de registros é maior que 1
```

## CASE

- Permite realizar condições e retornar valores diferentes com base nessas condições.

- Utilizado frequentemente para classificar dados

```sql
SELECT coluna,
    CASE
        WHEN condição1 THEN resultado1
        WHEN condição2 THEN resultado2
        ELSE resultado_padrao
    END AS alias_coluna
FROM TABELA;
-- Avalia as condições em ordem e retorna o resultado correspondente
-- Se nenhuma condição for atendida, retorna o resultado padrão
```

### Exemplo

```sql
SELECT nome,
    CASE
        WHEN idade < 18 THEN 'Menor de idade'
        WHEN idade BETWEEN 18 AND 60 THEN 'Adulto'
        ELSE 'Idoso'
    END AS faixa_etaria
FROM PESSOAS;
-- Classifica as pessoas em faixas etárias com base na idade
```
