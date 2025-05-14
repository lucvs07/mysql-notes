# Aula 05

## Alterar Estrutura Tabela

```sql
-- Adicionar uma nova coluna
ALTER TABLE nome_da_tabela
ADD nova_coluna VARCHAR(255);

-- Modificar uma coluna existente
ALTER TABLE nome_da_tabela
MODIFY coluna_existente INT NOT NULL;

-- Renomear uma coluna
ALTER TABLE nome_da_tabela
CHANGE coluna_antiga nova_coluna VARCHAR(255);

-- Remover uma coluna
ALTER TABLE nome_da_tabela
DROP COLUMN coluna_para_remover;
```

## Modificar Chaves e Índices

```sql
-- Adicionar Chave Primária
ALTER TABLE tabela ADD PRIMARY KEY (coluna);

-- Remover Chave Primária
ALTER TABLE tabela DROP PRIMARY KEY;

-- Adicionar Índices
ALTER TABLE tabela ADD INDEX nome_do_indice (coluna);

-- Elimar Índices
ALTER TABLE tabela DROP INDEX nome_do_indice;
```

## Alterações de Engenharia e Otimização

```sql
-- Mudar o Tipo de Tabela
ALTER TABLE tabela ENGINE = InnoDB;

-- Adicionar Chaves Estrangeiras
ALTER TABLE tabela ADD CONSTRAINT fk_nome_da_chave FOREIGN KEY (coluna) REFERENCES outra_tabela (coluna);

-- Modificar Opções da Tabela -> Como Conjunto de Caracteres e Collation
ALTER TABLE tabela CONVERT TO CHARACTER SET charset_name COLLATE collation_name;

```

## Excluir Dados

```sql
-- Excluir todos os dados de uma tabela
DELETE FROM nome_da_tabela;

-- Excluir dados com uma condição
DELETE FROM nome_da_tabela
WHERE coluna = 'valor';

-- Excluir todos os dados e resetar o auto incremento
TRUNCATE TABLE nome_da_tabela;
```

## Queries da Aula

```sql
-- Adicionar Coluna
ALTER TABLE proprietarios
ADD COLUMN qtd_hospedagens INT;

-- Alterar nome da tabela
ALTER TABLE alugueis RENAME TO reservas;

-- Alterar nome da coluna
ALTER TABLE reservas
RENAME COLUMN aluguel_id TO reserva_id;

-- Atualizar Dados na tabela Hospedagens
UPDATE hospedagens
SET ativo=1
WHERE hospedagem_id IN ('1', '10', '100');

-- Atualizar Dados na tabela proprietários
UPDATE proprietarios
SET contato = 'daniela_120@email.com'
WHERE proprietario_id = '1009';

-- Deletando Dados
DELETE FROM avaliacoes
WHERE hospedagem_id in ('10000', '1001');

DELETE FROM reservas
WHERE hospedagem_id in ('10000', '1001');

DELETE FROM hospedagens
WHERE hospedagem_id in ('10000', '1001');
```
