# Projeto SQL e Power BI - Análise de Dados de Hotelaria

## Descrição do Projeto

Este projeto tem como objetivo analisar dados de hotelaria e extrair insights valiosos para apoiar decisões estratégicas. Os dados foram inicialmente extraídos de arquivos Excel e inseridos em um banco de dados SQL. Em seguida, foram realizadas várias consultas SQL para transformar e preparar os dados para análise no Power BI. A análise incluiu questões relacionadas à receita por ano de cada hotel, união de dados de diferentes tabelas e criação de visões e dashboards informativos.

# Visual
![image](https://github.com/MatheusTorquete/Project-Hotels/assets/94683422/18ab75ad-4976-481a-9e03-ed7db5f6565b)


## Passos Realizados

### 1. **Inserção de Dados no Banco de Dados**

- **Origem dos Dados:** Os dados foram obtidos a partir de arquivos Excel.
  
- **Inserção no Banco de Dados:** Utilizamos uma tarefa automatizada do banco de dados para ler os arquivos Excel e inserir os dados em tabelas SQL.


### **Transformação e Preparação dos Dados no SQL**

- **Questão 1: Receita por Ano de Cada Hotel**

  ```sql
  select * from dbo.['2018$']
  union
  select * from dbo.['2019$']
  union
  select * from dbo.['2020$']
  
  select 
  arrival_date_year,
  hotel,
  round(sum((stays_in_week_nights + stays_in_weekend_nights) * adr), 2) AS Revenue 
  from hotels
  group by arrival_date_year, hotel
  ```

- **Questão 2: Unindo Dados de Hotéis, Vendas de Mercado e Custos de Refeições**

  ```sql
  select * from hotels
  left join dbo.market_segment$
  on hotels.market_segment = market_segment$.market_segment
  left join dbo.meal_cost$
  on hotels.meal = meal_cost$.meal
  ```

### 3. **Análise e Visualização no Power BI**

- **Receita Hoteleira ao Longo dos Anos:** Utilizamos funções DAX no Power BI para calcular e visualizar a receita hoteleira ao longo dos anos. Esta análise nos ajudou a entender se a receita dos hotéis está crescendo.

- **Estacionamento:** Utilizamos dados de ocupação e demanda para decidir se a expansão do estacionamento é necessária. Visualizamos padrões de ocupação ao longo do tempo e decidimos com base nesses dados.

- **Tendências nos Dados:** Utilizamos várias visualizações, como gráficos de linhas e gráficos de barras empilhadas, para identificar tendências nos dados. Isso incluiu padrões sazonais, comportamentos dos hóspedes e preferências de refeições.


## Conclusões e Resultados

Este projeto proporcionou insights valiosos sobre a receita dos hotéis, padrões de ocupação e preferências dos hóspedes. As análises realizadas no SQL e as visualizações interativas no Power BI nos permitiram tomar decisões informadas, como expansão de estacionamento e ajustes nas ofertas de refeições para atender às demandas dos clientes.


