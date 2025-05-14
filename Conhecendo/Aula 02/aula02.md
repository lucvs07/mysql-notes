# Estruturando o Banco De Dados

## Criando a Database

```sql
-- Criando um banco de dados chamado 'meu_banco'
CREATE SCHEMA `meu_banco` DEFAULT CHARACTER SET utf8 COLLATE utf8_bin ;
-- OU
CREATE DATABASE `meu_banco` DEFAULT CHARACTER SET utf8 COLLATE utf8_bin ;
-- Usando o banco de dados criado
USE meu_banco;
```

## Criando Tabelas

```sql
CREATE TABLE tabela_1 (
chave_primaria_tb_1 VARCHAR(255) PRIMARY KEY,
campo1 VARCHAR(255),
campo2 VARCHAR(20),
campo3 VARCHAR(255)
);
-- Criando com FK
CREATE TABLE tabela_2 (
chave_primaria_tb_2 VARCHAR(255) PRIMARY KEY,
campo1 VARCHAR(255),
campo2 VARCHAR(20),
campo3 VARCHAR(255),
FOREIGN KEY (chave_tb_1) REFERENCES tabela_1(chave_primaria_tb_1)
);
```

## Tipos de Dados Comum

| Tipo de Dado       | Descrição                                                                 |
|--------------------|---------------------------------------------------------------------------|
| INT                | Número inteiro.                                                         |
| VARCHAR(n)         | Cadeia de caracteres com tamanho variável, até o limite `n`.            |
| CHAR(n)            | Cadeia de caracteres com tamanho fixo, definido por `n`.                |
| TEXT               | Texto de tamanho variável, usado para grandes quantidades de texto.     |
| DATE               | Data no formato `YYYY-MM-DD`.                                           |
| DATETIME           | Data e hora no formato `YYYY-MM-DD HH:MM:SS`.                           |
| TIMESTAMP          | Data e hora com fuso horário, usado para marcações temporais.           |
| DECIMAL(m, d)      | Número decimal com `m` dígitos no total e `d` dígitos após o ponto.      |
| FLOAT              | Número de ponto flutuante.                                              |
| BOOLEAN            | Valor lógico, `TRUE` ou `FALSE`.                                        |

## Populando Tabelas

```sql
-- Inserindo dados na tabela_1
INSERT INTO tabela_1 (chave_primaria_tb_1, campo1, campo2, campo3)
VALUES ('id1', 'valor1', '12345', 'valor3');

-- Inserindo dados na tabela_2 com chave estrangeira
INSERT INTO tabela_2 (chave_primaria_tb_2, campo1, campo2, campo3, chave_tb_1)
VALUES ('id2', 'valorA', '67890', 'valorC', 'id1');
```
