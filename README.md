# billing-dw-design
design, modelling of a datawarehouse -  facts and dimension tables (star-schema) for a cloud-service-provider dataset 



## objective:

To design a data warehouse that can support the queries for more analysis:

* average billing per customer
* billing by country
* top 10 customers
* top 10 countries
* billing by industry
* billing by category
* billing by year
* billing by month
* billing by quarter
* average billing per industry per month
* average billing per industry per quarter
* average billing per country per quarter
* average billing per country per industry per quarter

## Tools Used:
* postgres
* Vscode

## Process:

1. Ingest data from cloud-service-provider. csv
2. Connect to postgres
3. design facts and dimension table (Schema.sql)
4. Solve queries
