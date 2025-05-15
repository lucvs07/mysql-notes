# Comando SQL `LIKE`

O comando `LIKE` no SQL é usado em consultas para buscar registros em uma tabela que correspondam a um padrão específico. Ele é frequentemente utilizado com as cláusulas `WHERE` ou `HAVING` para realizar buscas baseadas em padrões de texto.

## Sintaxe Básica

```sql
SELECT coluna1, coluna2, ...
FROM tabela
WHERE coluna LIKE padrão;
```

- `coluna`: A coluna onde será feita a busca.
- `padrão`: O padrão que será comparado com os valores da coluna.

## Caracteres Coringa

O `LIKE` utiliza dois caracteres coringa principais para definir padrões:

1. **`%`**: Representa zero, um ou mais caracteres.
2. **`_`**: Representa exatamente um caractere.

## Exemplos

### 1. Busca por valores que começam com um padrão

```sql
SELECT * 
FROM clientes
WHERE nome LIKE 'Jo%';
```

**Explicação**: Retorna todos os registros onde a coluna `nome` começa com "Jo", como "João", "José", etc.

---

### 2. Busca por valores que terminam com um padrão

```sql
SELECT * 
FROM produtos
WHERE descricao LIKE '%fone';
```

**Explicação**: Retorna todos os registros onde a coluna `descricao` termina com "fone", como "telefone", "microfone", etc.

---

### 3. Busca por valores que contêm um padrão

```sql
SELECT * 
FROM livros
WHERE titulo LIKE '%aventura%';
```

**Explicação**: Retorna todos os registros onde a coluna `titulo` contém "aventura", como "Uma grande aventura", "Aventura no espaço", etc.

---

### 4. Busca por valores com um caractere específico

```sql
SELECT * 
FROM usuarios
WHERE username LIKE 'a_a';
```

**Explicação**: Retorna todos os registros onde a coluna `username` tem exatamente 3 caracteres, começando com "a" e terminando com "a", como "ana", "ada", etc.

---

### 5. Combinação de padrões

```sql
SELECT * 
FROM emails
WHERE endereco LIKE '%@gmail.com';
```

**Explicação**: Retorna todos os registros onde a coluna `endereco` termina com "@gmail.com".

---

## Considerações

- O comando `LIKE` não diferencia maiúsculas de minúsculas em bancos de dados como MySQL, a menos que o collation da coluna seja sensível a maiúsculas/minúsculas.
- Para buscas mais avançadas, considere o uso de expressões regulares com o comando `REGEXP`.
