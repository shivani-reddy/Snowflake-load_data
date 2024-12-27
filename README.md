# Snowflake-load_data

https://app.snowflake.com/qsjfhpg/njb59078/w2r5TEfMxxmS#query



Summary and key points
In summary, you used a pre-loaded worksheet in Snowsight to complete the following steps:

Set the role and warehouse context.

Create a database, schema, and table.

Create a stage and load the data from the stage into the database.

Query the data.

Here are some key points to remember about loading and querying data:

You need the required permissions to create and manage objects in your account. In this tutorial, you use the ACCOUNTADMIN system role for these privileges.

This role is not normally used to create objects. Instead, we recommend creating a hierarchy of roles aligned with business functions in your organization. For more information, see Using the ACCOUNTADMIN Role.

You need a warehouse for the resources required to create and manage objects and run SQL commands. This tutorial uses the compute_wh warehouse included with your trial account.

You created a database to store the data and a schema to group the database objects logically.

You created a stage to load data from a CSV file.

After the data was loaded into your database, you queried it using SELECT statements.



TASTY_BYTES_SAMPLE_DATA--use this command for selecting the role 
USE ROLE accountadmin;

--use this command for selecting the warehouse
USE WAREHOUSE compute_wh;
--create the database
CREATE DATABASE tasty_bytes_sample_data;
--create the schema
CREATE SCHEMA tasty_bytes_sample_data.raw_pos;

CREATE OR REPLACE TABLE tasty_bytes_sample_data.raw_pos.menu
(
    menu_id NUMBER(19,0),
    menu_type_id NUMBER(38,0),
    menu_type VARCHAR(16777216),
    truck_brand_name VARCHAR(16777216),
    menu_item_id NUMBER(38,0),
    menu_item_name VARCHAR(16777216),
    item_category VARCHAR(16777216),
    item_subcategory VARCHAR(16777216),
    cost_of_goods_usd NUMBER(38,4),
    sale_price_usd NUMBER(38,4),
    menu_item_health_metrics_obj VARIANT
);

SELECT * FROM tasty_bytes_sample_data.raw_pos.menu;


CREATE OR REPLACE STAGE tasty_bytes_sample_data.public.blob_stage
url = 's3://sfquickstarts/tastybytes/'
file_format = (type = csv);


LIST @tasty_bytes_sample_data.public.blob_stage/raw_pos/menu/;


COPY INTO tasty_bytes_sample_data.raw_pos.menu
FROM @tasty_bytes_sample_data.public.blob_stage/raw_pos/menu/;


SELECT COUNT(*) AS row_count FROM tasty_bytes_sample_data.raw_pos.menu;

SELECT TOP 10 * FROM tasty_bytes_sample_data.raw_pos.menu;

DROP DATABASE IF EXISTS tasty_bytes_sample_data;



