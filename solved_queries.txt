1. Average Billing Per Customer:

SELECT "DimCustomer".customerid, "DimCustomer".category, AVG("FactBilling".billedamount) AS avg_billing
FROM "DimCustomer"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
GROUP BY "DimCustomer".customerid, "DimCustomer".category
ORDER BY avg_billing DESC;



2.Billing by Country:

SELECT "DimCustomer".country, SUM("FactBilling".billedamount) AS total_billing
FROM "DimCustomer"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
GROUP BY "DimCustomer".country
ORDER BY total_billing DESC;


3. Top 10 Customers:

SELECT "DimCustomer".customerid, "DimCustomer".category, SUM("FactBilling".billedamount) AS total_billing
FROM "DimCustomer"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
GROUP BY "DimCustomer".customerid, "DimCustomer".category
ORDER BY total_billing DESC
LIMIT 10;


4. Top 10 Countries:

SELECT "DimCustomer".country, SUM("FactBilling".billedamount) AS total_billing
FROM "DimCustomer"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
GROUP BY "DimCustomer".country
ORDER BY total_billing DESC
LIMIT 10;






5. Billing by Industry:


SELECT "DimCustomer".industry, SUM("FactBilling".billedamount) AS total_billing
FROM "DimCustomer"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
GROUP BY "DimCustomer".industry;





6 Billing by Category:

SELECT "DimCustomer".category, SUM("FactBilling".billedamount) AS total_billing
FROM "DimCustomer"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
GROUP BY "DimCustomer".category;



Billing by Year:

SELECT EXTRACT(YEAR FROM "DimMonth".monthname) AS billing_year, SUM("FactBilling".billedamount) AS total_billing
FROM "DimMonth"
LEFT JOIN "FactBilling" ON "DimMonth".monthid = "FactBilling".monthid
GROUP BY billing_year
ORDER BY billing_year;



Average Billing Per Industry Per Month:

SELECT "DimCustomer".industry, "DimMonth".monthname, AVG("FactBilling".billedamount) AS avg_billing
FROM "DimCustomer"
CROSS JOIN "DimMonth"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
    AND "DimMonth".monthid = "FactBilling".monthid
GROUP BY "DimCustomer".industry, "DimMonth".monthname
ORDER BY "DimCustomer".industry, "DimMonth".monthid;




Average Billing Per Industry Per Quarter:

SELECT "DimCustomer".industry, "DimMonth".quartername, AVG("FactBilling".billedamount) AS avg_billing
FROM "DimCustomer"
CROSS JOIN "DimMonth"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
    AND "DimMonth".monthid = "FactBilling".monthid
GROUP BY "DimCustomer".industry, "DimMonth".quartername
ORDER BY "DimCustomer".industry, "DimMonth".quarter;



Average Billing Per Country Per Quarter:

SELECT "DimCustomer".country, "DimMonth".quartername, AVG("FactBilling".billedamount) AS avg_billing
FROM "DimCustomer"
CROSS JOIN "DimMonth"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
    AND "DimMonth".monthid = "FactBilling".monthid
GROUP BY "DimCustomer".country, "DimMonth".quartername
ORDER BY "DimCustomer".country, "DimMonth".quarter;


Average Billing Per Country Per Industry Per Quarter:

SELECT "DimCustomer".country, "DimCustomer".industry, "DimMonth".quartername, AVG("FactBilling".billedamount) AS avg_billing
FROM "DimCustomer"
CROSS JOIN "DimMonth"
LEFT JOIN "FactBilling" ON "DimCustomer".customerid = "FactBilling".customerid
    AND "DimMonth".monthid = "FactBilling".monthid
GROUP BY "DimCustomer".country, "DimCustomer".industry, "DimMonth".quartername
ORDER BY "DimCustomer".country, "DimCustomer".industry, "DimMonth".quarter;
