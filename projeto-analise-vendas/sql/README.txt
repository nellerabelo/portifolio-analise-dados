-- 1. ANÁLISE DE FATURAMENTO POR CIDADE
-- Objetivo: Identificar qual filial gera mais receita para a empresa.
SELECT 
    City, 
    SUM(Total) AS Faturamento_Total,
    AVG(Rating) AS Media_Avaliacao
FROM vendas
GROUP BY City
ORDER BY Faturamento_Total DESC;

-- 2. PERFIL DO CLIENTE E MÉTODO DE PAGAMENTO
-- Objetivo: Entender como os membros vs. clientes normais preferem pagar.
SELECT 
    "Customer type", 
    Payment, 
    COUNT(*) AS Quantidade_Transacoes
FROM vendas
GROUP BY "Customer type", Payment
ORDER BY "Customer type", Quantidade_Transacoes DESC;

-- 3. ANÁLISE DE MARGEM DE LUCRO POR LINHA DE PRODUTO
-- Objetivo: Descobrir quais produtos são mais lucrativos, não apenas os que vendem mais.
SELECT 
    "Product line", 
    ROUND(SUM("gross income"), 2) AS Lucro_Bruto_Total,
    ROUND(AVG("gross margin percentage"), 2) AS Margem_Media
FROM vendas
GROUP BY "Product line"
ORDER BY Lucro_Bruto_Total DESC;
