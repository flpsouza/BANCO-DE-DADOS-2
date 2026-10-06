-- Query 1
SELECT id, nome, email, data_cadastro
FROM clientes
ORDER BY data_cadastro DESC
LIMIT 100;

-- Query 2
SELECT id_cliente, rua, bairro
FROM enderecos
WHERE estado = 'SP'
  AND cidade = 'Campinas';

-- Query 3
SELECT p.id, c.nome, p.valor_total
FROM pedidos p
INNER JOIN clientes c ON c.id = p.id_cliente
WHERE p.data_pedido >= '2026-01-01'
  AND p.data_pedido < '2027-01-01';

-- Query 4
SELECT estado, cidade
FROM userinfo
WHERE estado = 'SP';

-- Query 5
SELECT
    c.id,
    c.nome,
    SUM(p.valor) AS total_gasto,
    MAX(p.data_pedido) AS data_ultimo_pedido
FROM clientes c
INNER JOIN pedidos p ON p.id_cliente = c.id
WHERE c.data_cadastro >= '2023-01-01'
  AND c.status = 'ativo'
GROUP BY c.id, c.nome
ORDER BY total_gasto DESC;

-- Query 6
SELECT p.nome, c.nome_categoria
FROM produtos p
INNER JOIN categorias c ON c.id = p.id_categoria;

-- Query 7
SELECT id, status, total
FROM faturas
WHERE data_criacao >= '2026-03-01'
  AND data_criacao < '2026-04-01';

-- Query 8
SELECT id, valor, status
FROM transacoes
WHERE codigo_transacao = '9845720194';

-- Query 9
SELECT DISTINCT c.id, c.nome, c.email
FROM clientes c
INNER JOIN pedidos p ON p.id_cliente = c.id
INNER JOIN produtos pr ON pr.id = p.id_produto
WHERE pr.categoria = 'Eletronicos';

-- Query 10
SELECT c.id, c.nome, p.id AS pedido_id, p.valor_total
FROM clientes c
INNER JOIN pedidos p ON p.id_cliente = c.id
WHERE p.status = 'faturado'
  AND p.valor_total > 500;
