# Linguagem de Consulta Estruturada (SQL)

SQL (Structured Query Language) é uma linguagem padrão para gerenciar bancos de dados relacionais, o que significa que você pode usar o mesmo conjunto de comandos para trabalhar com diferentes sistemas de gerenciamento de banco de dados (SGBDs), como MySQL, PostgreSQL, Oracle, etc.

SQL oferece flexibilidade para criar consultas complexas e manipular dados de diversas maneiras.  
Embora tenha uma sintaxe específica, SQL é relativamente fácil de aprender em comparação com outras linguagens de programação.

## 📌 SQL ANSI - Comandos Fundamentais

| Categoria | Comando | Descrição |
| --- | --- |--- |
| **DDL** (Data Definition Language) | [`CREATE`](#create) | Cria objetos no banco (tabelas, views, índices, esquemas, domínios, etc.) |
|  | [`ALTER`](#alter) | Modifica a estrutura de objetos existentes (ex: adicionar/remover coluna, mudar tipo de dado) |
|  | [`DROP`](#drop) | Remove objetos permanentemente do banco |
|  | [`TRUNCATE`](#truncate) | Remove todos os registros de uma tabela, mantendo a estrutura (mais rápido que `DELETE`) |
|  | [`RENAME`](#rename) | Renomeia tabelas, colunas ou outros objetos do banco |
|  | [`COMMENT`](#comment) | Adiciona comentários de documentação em objetos do banco |
| **DML** (Data Manipulation Language) | [`INSERT`](#insert) | Insere novos registros em uma tabela |
|  | [`UPDATE`](#update) | Atualiza registros existentes em uma tabela |
|  | [`DELETE`](#delete) | Remove registros de uma tabela |
|  | [`MERGE`](#merge) | Executa `INSERT` ou `UPDATE` dependendo se o registro já existe (UPSERT) |
| **DQL** (Data Query Language) | [`SELECT`](#select) | Consulta dados em uma ou mais tabelas; pode incluir filtros, ordenação, agregação, junções etc. |
| **DCL** (Data Control Language) | [`GRANT`](#grant) | Concede permissões de acesso a usuários/roles |
|  | [`REVOKE`](#revoke) | Remove permissões concedidas |
| **TCL** (Transaction Control Language) | `COMMIT` | Confirma as operações de uma transação (torna permanente) |
|  | `ROLLBACK` | Desfaz as operações não confirmadas de uma transação |
|  | `SAVEPOINT` | Define pontos de restauração dentro de uma transação |
|  | `SET TRANSACTION` | Define propriedades de uma transação (ex: nível de isolamento, leitura apenas, etc.) |

## 📌 SQL ANSI - Cláusulas e Operadores Fundamentais

| Tipo | Palavra-chave | Descrição |
| --- | --- | --- |
| Cláusula | `FROM` | Define de onde os dados vêm (tabela ou subconsulta) |
|  | `WHERE` | Filtra linhas antes da agregação |
|  | `JOIN ... ON` | Junta tabelas (`INNER`, `LEFT`, `RIGHT`, `FULL`, `CROSS`) |
|  | `GROUP BY` | Agrupa linhas para funções de agregação |
|  | `HAVING` | Filtra grupos após agregação |
|  | `ORDER BY` | Ordena o resultado final |
|  | `DISTINCT` | Remove duplicatas do resultado |
|  | `WITH` (CTE) | Cria consultas temporárias nomeadas |
|  | `UNION` / `INTERSECT` / `EXCEPT` | Operações de conjunto (união, interseção, diferença) |
|  | `OFFSET … FETCH` | Paginação ANSI |
| Predicado | `LIKE` | Busca por padrão em string |
|  | `IN` / `NOT IN` | Verifica pertencimento a lista ou subconsulta |
|  | `BETWEEN` | Verifica se valor está em um intervalo |
|  | `IS NULL` / `IS NOT NULL` | Testa nulos |
|  | `EXISTS` | Verifica se subconsulta retorna linhas |
|  | `ANY` / `ALL` | Compara valor com conjunto de resultados |
|  | `AND` / `OR` / `NOT` | Operadores lógicos |
| Expressão | `CASE` | Estrutura condicional dentro de consultas |
| Controle de sessão | `SET SCHEMA` | Define schema padrão (ANSI) |
|  | `USE` | Não ANSI (MySQL/SQL Server) muda o banco em uso |

## 📌 SQL ANSI - Exemplos

### CREATE

```sql
CREATE TABLE clients (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);
```

### ALTER

```sql
ALTER TABLE clients ADD email VARCHAR(150);
```

### DROP

```sql
DROP TABLE clients;
```

### TRUNCATE

```sql
TRUNCATE TABLE clients;
```

### RENAME

```sql
ALTER TABLE clients RENAME TO customers;
```

### COMMENT

```sql
COMMENT ON COLUMN clients.name IS 'Client''s full name';
```

### INSERT

```sql
INSERT INTO clients(id, name, age) VALUES (1, 'Anna', 27);
```

### UPDATE

```sql
UPDATE clients SET age = 28 WHERE = 1;
```

### DELETE

```sql
DELETE FROM clients WHERE id = 1;
```

### MERGE

```sql
MERGE INTO clients c
USING (SELECT 1 AS id, 'Anna' AS name, 28 AS age) s
ON (c.id = s.id)
WHEN MATCHED THEN UPDATE SET name = s.name, age = s.age
WHEN NOT MATCHED THEN INSERT(id, name, age)
VALUES(s.id, s.name, s.age);
```

### SELECT

```sql
SELECT name, age
FROM clients
WHERE age > 20
ORDER BY age;
```

### GRANT

```sql
GRANT SELECT, INSERT ON clients TO user_test;
```

### REVOKE

```sql
REVOKE INSERT ON clients FROM user_test;
```

