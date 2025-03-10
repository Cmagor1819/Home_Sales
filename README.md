# Home_Sales

# Objective: In this challenge, you'll use your knowledge of SparkSQL to determine key metrics about home sales data. Then you'll use Spark to create temporary views, partition the data, cache and uncache a temporary table, and verify that the table has been uncached.

# Part 1: 

In this section we focus on importing all of our dependencies, the os, installing spark and java, setting environment variables, and starting the spark session.

# Part 2: 

In this section we read in the home_sales_revised csv file and transform it into a PySpark DataFrame. Then we create a temporary view of the DataFrame to be able to be able to answer the following questions:

 * What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.

 * What is the average price of a home for each year the home was built, that has three bedrooms and three bathrooms? Round off your answer to two decimal places.

 * What is the average price of a home for each year the home was built, that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.

 * What is the average price of a home per "view" rating having an average home price greater than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.

# Part 3:

For the next section, we cache our temporary table 'home_sales' and check if the table has been cached. We then run the same query for the fourth question to compare the runtime to the uncached runtime.

# Part 4:

Next, we partition by the 'date_built' field on the formatted parquet home sales data, read in the parquet formatted data and create a temporary table for the parquet data.

# Part 5:

For the final part, we run the same query as last time to answer the fourth question from above and compare the runtime to the cached runtime. Next, we uncache the home_sales temporary table and check to make sure it has been uncached.

# I got/referenced the following lines of code from Xpert Learning Assistant:

* home_sales_df.write.partitionBy("date_built").mode("overwrite").parquet("parquet_home_sales")

* spark.sql("SELECT ROUND(AVG(price),2), view FROM home_sales GROUP BY view HAVING ROUND(AVG(price),2) >= 350000 ORDER BY view DESC").show()
