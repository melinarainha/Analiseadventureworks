# Analiseadventureworks
Projeto de Análise Financeira com Base de Dados Fictícia

1-	Objetivo 
Avaliar o desempenho de vendas de uma empresa fictícia através de indicadores gerais, comparação de receita ao longo do tempo, análise por região, por produto e por cliente.

2 – Visão geral do relatório
A primeira página do dashboard conta com KPI’s de receita total, lucro total, lucro%, ticket médio e total de pedidos, sendo todos os visuais interativos e podendo ser filtrados por ano. As páginas seguintes contam com gráficos que comparam as receitas por mês (ano a ano), tabelas e gráficos destacando os principais produtos com maior receita, mapa de receita por região, tabelas e gráficos destacando os clientes mais lucrativos.

3-Fonte de Dados
Base AdventureWorks2022
Volume de dados: 8 tabelas, tendo a maior delas 60.855 linhas

4- Transformações no Power Query
Foi realizada apenas uma conferência do formato dos dados, cabeçalho e duplicidades, já que os dados vieram parcialmente organizados.

5- Medidas DAX criadas

CustoTotal = SUM(FactInternetSales[TotalProductCost])
Lucro% = DIVIDE([LucroTotal],[ReceitaTotal])*100

LucroTotal = [ReceitaTotal]-[CustoTotal]

ReceitaMesAno = CALCULATE(SUM(FactInternetSales[SalesAmount]),VALUES(FactInternetSales[MesAno]))

ReceitaTotal = SUM(FactInternetSales[SalesAmount])

TicketMedio = DIVIDE([ReceitaTotal],[TotalClientes])

TotalClientes = DISTINCTCOUNT(DimCustomer[CustomerKey])

TotalPedidos = DISTINCTCOUNT(FactInternetSales[SalesOrderNumber])

TotalVendas = SUM(FactInternetSales[OrderQuantity])

TotalVendedores = DISTINCTCOUNT(DimEmployee[EmployeeKey])

MesAno = FORMAT(FactInternetSales[OrderDate],"MMMM/YYYY")

MesNome = FORMAT(FactInternetSales[OrderDate],"MMM")

NomeCliente = 
 LOOKUPVALUE(DimCustomer[NomeCompleto],
 DimCustomer[CustomerKey],
 FactInternetSales[CustomerKey])
 
NomeCompleto = DimCustomer[FirstName]&" "&DimCustomer[LastName]

6- Visuais Utilizados
- Cartões para destacar os principais KPI’s;
- Slicer para filtrar os visuais por ano;
- Gráficos de linhas;
- Gráficos de barras para comparativo ano a ano;
- Tabelas para destacar as principais informações de cada etapa;
- Treemaps de top 10;
- Gráfico de barras horizontais;
- Gráfico de rosca;
- Mapa para a distribuição de receita por território;
- Slicer de produto por cliente;
- Destaque melhor cliente por receita.

7- Principais Insights
- O mês com melhor receita foi dezembro de 2013;
- O produto com mais unidades vendidas foi a water bottle – 30 oz, já o produto que gerou mais receita foi a mountain 200- black;
- O país com maior receita foi os EUA.
