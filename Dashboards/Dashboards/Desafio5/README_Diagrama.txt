
# Processo de Construção do Diagrama

Esse diagrama foi criado usando um esquema estrela, que é um jeito bem comum de organizar os dados em projetos de BI.

## 1. Identificação das Tabelas Fato e Dimensões:
   - **Tabela Fato (`F_Vendas`)**:
     - Essa é a tabela principal do esquema estrela, onde ficam os dados das transações que a gente quer analisar. Aqui, temos colunas como `Sales`, `Country`, `Date`, `Discount Band`, `Discounts`, `Gross Sales`, `ID_produto`, `Month Name`, e `Product`.
     
   - **Tabelas Dimensão**:
     - Essas tabelas dão mais contexto para as vendas da tabela fato. Elas são conectadas à tabela fato por meio de chaves estrangeiras.
     - **`D_Produtos_Detalhes`**: Traz informações detalhadas dos produtos, como `ID_produto`, `Manufacturing Price`, `Sale Price`, `Units Sold`, etc.
     - **`D_Produto`**: Mostra informações agregadas dos produtos, como médias, medianas e valores máximos de vendas.
     - **`D_Detalhes`**: Inclui dados como `Sales`, `COGS`, `Country`, `Manufacturing Price`, `Profit`, `Segment`, etc.
     - **`D_Desconto`**: Foca nos descontos, trazendo informações como `Discount Band`, `Discounts`, e `ID_produto`.
     - **`Table Date`**: É a tabela de datas, essencial para analisar o tempo nas vendas, com colunas como `Date`, `Day of the week`, `Month Number`, `Week Number`, entre outras.

## 2. Criação das Relações:
   - Cada tabela de dimensão foi conectada à tabela fato `F_Vendas` usando chaves estrangeiras. Por exemplo, `ID_produto` na tabela fato está ligado ao `ID_produto` nas tabelas de dimensão `D_Produtos_Detalhes` e `D_Produto`.
   - A `Table Date` foi conectada à coluna `Date` da tabela fato `F_Vendas`, permitindo que a gente analise as vendas ao longo do tempo.

## 3. Uso de Funções DAX:
   - A função `CALENDAR` foi usada para criar a tabela `Table Date`, que é super importante para as análises temporais.
   - Outras funções DAX, como `DATE` e `FORMAT`, foram usadas para criar e formatar as datas, permitindo que o nome do dia da semana apareça por extenso (com o formato `"DDDD"`).


Com esse esquema, os dados ficam organizados de um jeito que facilita bastante a criação de relatórios e análises no Power BI. O esquema estrela ajuda a simplificar as consultas e melhorar o desempenho.
