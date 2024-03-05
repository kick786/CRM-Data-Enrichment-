-- Example SQL script to enrich customer data with demographic information

-- Step 1: Connect to external data source (e.g., demographics database)
SELECT *
FROM external_database.demographics
WHERE city = 'Bangalore';

-- Step 2: Join external data with CRM customer data
UPDATE crm_customer
SET crm_customer.age = demographics.age,
    crm_customer.gender = demographics.gender
FROM crm_customer
JOIN external_database.demographics
ON crm_customer.city = demographics.city
AND crm_customer.zip_code = demographics.zip_code;
