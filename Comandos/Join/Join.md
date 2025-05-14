# Comando JOIN no SQL

O comando `JOIN` no SQL é usado para combinar registros de duas ou mais tabelas com base em uma condição relacionada entre elas. Existem diferentes tipos de `JOIN`, cada um com uma finalidade específica.

## Tipos de JOIN

### 1. INNER JOIN

Retorna apenas os registros que possuem correspondência em ambas as tabelas.

```sql
SELECT A.nome, B.departamento
FROM funcionarios A
INNER JOIN departamentos B
ON A.departamento_id = B.id;
```

**Exemplo:**

- Tabela `funcionarios`:

    | id | nome    | departamento_id |
    |----|---------|-----------------|
    | 1  | Ana     | 1               |
    | 2  | João    | 2               |
    | 3  | Maria   | NULL            |

- Tabela `departamentos`:

    | id | departamento |
    |----|--------------|
    | 1  | RH           |
    | 2  | TI           |

**Resultado:**
    | nome  | departamento |
    |-------|--------------|
    | Ana   | RH           |
    | João  | TI           |

---

### 2. LEFT JOIN (ou LEFT OUTER JOIN)

Retorna todos os registros da tabela à esquerda e os registros correspondentes da tabela à direita. Se não houver correspondência, os valores da tabela à direita serão `NULL`.

```sql
SELECT A.nome, B.departamento
FROM funcionarios A
LEFT JOIN departamentos B
ON A.departamento_id = B.id;
```

**Resultado:**
    | nome  | departamento |
    |-------|--------------|
    | Ana   | RH           |
    | João  | TI           |
    | Maria | NULL         |

---

### 3. RIGHT JOIN (ou RIGHT OUTER JOIN)

Retorna todos os registros da tabela à direita e os registros correspondentes da tabela à esquerda. Se não houver correspondência, os valores da tabela à esquerda serão `NULL`.

```sql
SELECT A.nome, B.departamento
FROM funcionarios A
RIGHT JOIN departamentos B
ON A.departamento_id = B.id;
```

**Resultado:**
    | nome  | departamento |
    |-------|--------------|
    | Ana   | RH           |
    | João  | TI           |

---

### 4. FULL JOIN (ou FULL OUTER JOIN)

Retorna todos os registros quando há correspondência em uma das tabelas ou em ambas. Onde não houver correspondência, os valores serão `NULL`.

```sql
SELECT A.nome, B.departamento
FROM funcionarios A
FULL JOIN departamentos B
ON A.departamento_id = B.id;
```

**Resultado:**
    | nome  | departamento |
    |-------|--------------|
    | Ana   | RH           |
    | João  | TI           |
    | Maria | NULL         |

---

### Observação

Nem todos os bancos de dados suportam `FULL JOIN`. Em alguns casos, pode ser necessário combinar `LEFT JOIN` e `RIGHT JOIN` com `UNION`.
