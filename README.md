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

