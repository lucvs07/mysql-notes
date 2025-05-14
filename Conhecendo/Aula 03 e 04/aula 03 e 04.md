# Queries da Aula

```sql

SELECT * FROM avaliacoes WHERE nota >= 4;

SELECT * FROM hospedagens WHERE tipo = 'hotel' AND ativo = 1;

-- Query para buscar valor médio dentre os aluguéis
SELECT cliente_id, AVG(preco_total) AS ticket_medio
FROM alugueis
GROUP BY cliente_id;

-- Query para buscar o valor médio de dias contratados
SELECT cliente_id,
AVG(DATEDIFF(data_fim, data_inicio)) AS media_dias_estadia
FROM alugueis
GROUP BY cliente_id
ORDER BY media_dias_estadia DESC;

-- Query para buscar clientes com mais reservas
SELECT c.nome, COUNT(*) AS total_reservas 
FROM alugueis a
JOIN clientes c ON a.cliente_id = c.cliente_id
GROUP BY c.nome
ORDER BY total_reservas DESC;

-- Query para buscar proprietarios com hospedagens ativas
SELECT p.nome AS proprietario,
COUNT(h.hospedagem_id) AS total_hospedagens_ativas
FROM proprietarios p
JOIN hospedagens h ON p.proprietario_id = h.proprietario_id
WHERE h.ativo = 1
GROUP BY p.nome
ORDER BY total_hospedagens_ativas DESC
LIMIT 10;

-- Query para buscar propriedades inativas
SELECT p.nome AS proprietario, COUNT(*) as total_hospedagens_inativas
FROM proprietarios p
JOIN hospedagens h ON p.proprietario_id = h.proprietario_id
WHERE h.ativo = 0
GROUP BY p.nome
ORDER BY total_hospedagens_inativas DESC;

-- Query para buscar datas atrativas
SELECT YEAR(data_inicio) AS ano,
MONTH(data_inicio) AS mes,
COUNT(*) AS total_alugueis
from alugueis
GROUP BY ano, mes
ORDER BY total_alugueis DESC;
```
