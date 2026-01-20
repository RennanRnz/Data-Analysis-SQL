# SQL para Análise de Dados 📊

Este repositório contém recursos, consultas e melhores práticas para a utilização do SQL como ferramenta central na análise de dados. O objetivo é transformar dados brutos em insights acionáveis através de manipulação eficiente e consultas estruturadas.

## 🚀 Por que SQL para Data Analytics?

O SQL (Structured Query Language) é a linguagem fundamental para analistas de dados. Enquanto ferramentas de BI (Power BI, Tableau) visualizam dados, o SQL é responsável por:
- Extrair dados de grandes bancos de dados (Big Data).
- Limpar e transformar dados (ETL).
- Realizar agregações complexas e cálculos estatísticos.
- Unir fontes de dados distintas.

## 🛠️ Principais Comandos e Técnicas

### 1. Exploração e Filtragem
Uso de `SELECT`, `FROM`, `WHERE`, `DISTINCT` e operadores lógicos para entender a estrutura dos dados.

### 2. Agregações e Métricas
Cálculo de KPIs utilizando `GROUP BY` e funções de agregação:
- `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`.
- `HAVING` para filtrar dados agregados.

### 3. Joins (União de Tabelas)
Relacionamento entre tabelas para visão holística:
- `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL OUTER JOIN`.

### 4. Análises Avançadas
- **Window Functions:** Uso de `OVER()`, `PARTITION BY`, `RANK()`, e `LAG/LEAD` para análises de séries temporais e ranking.
- **CTEs (Common Table Expressions):** Organização de consultas complexas com `WITH`.
- **Subqueries:** Consultas aninhadas para lógica multicamada.
- **Case Statements:** Criação de colunas condicionais e segmentação de dados.

## 📂 Estrutura do Projeto

*   `/scripts`: Consultas SQL organizadas por caso de uso (ex: retenção de clientes, análise de vendas).
*   `/data`: Dicionário de dados ou amostras (se aplicável).
*   `/reports`: Insights extraídos a partir das consultas.

## 📈 Exemplo de Consulta: Análise de Crescimento Mensal

```sql
WITH MonthlySales AS (
    SELECT 
        DATE_TRUNC('month', order_date) AS month,
        SUM(total_amount) AS revenue
    FROM orders
    GROUP BY 1
)
SELECT 
    month,
    revenue,
    LAG(revenue) OVER (ORDER BY month) AS prev_month_revenue,
    (revenue - LAG(revenue) OVER (ORDER BY month)) / LAG(revenue) OVER (ORDER BY month) * 100 AS growth_pct
FROM MonthlySales;
```
## 🔗 Recursos Úteis

*   **[Documentação Oficial do PostgreSQL](https://www.postgresql.org):** Manual completo para consulta de sintaxe, funções avançadas e administração de um dos bancos de dados mais robustos do mercado.
*   **[W3Schools SQL Tutorial](https://www.w3schools.com):** Um guia prático e interativo ideal para iniciantes revisarem comandos básicos e testarem queries diretamente no navegador.
*   **[Mode Analytics SQL Tutorial](https://app.mode.com):** Um dos melhores recursos focados especificamente em **Análise de Dados**, cobrindo desde o básico até funções de janela (Window Functions).
*   **[Kaggle SQL Courses](https://www.kaggle.com):** Cursos práticos focados em manipular grandes conjuntos de dados utilizando SQL voltado para Data Science.

