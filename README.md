# Module 22 Challenge: Home Sales Metrics 
The purpose of this challenge is to determine certain key metrics about home sales using SparkSQL to query the data, and then Spark for quicker querying by creating temporary views, partitioning the data, caching and uncaching temporary tables, and verifying proper uncaching of tables. 

## Query Process 
To begin the analysis, I imported all necessary PySpark SQL functions, read the home_sales_revised.csv into a Spark DataFrame, verified that the schema was correct for each column, and created a temporary table 'home_sales' on which I performed four queries (see Results section below). For the last query, I recorded the time it took to run so I could compare against a cached table and a partitioned table. 

After the last query was ran, I cached the 'home_sales' table and ran the fourth query again, recording the time it took. Next, I partitioned the original 'home_sales_df' by 'date_built', stored this in the parquet data format, and created a temporary table with this data. I ran the fourth query one last time, again recording the time it took to run.

Once all queries were complete, I uncached the table and verified uncaching before ending the analysis.

## Results
**What is the average price for a 4-bedroom house sold for each year?**

The analysis found the average price for 4-bedroom homes is $296,363.88 (2022), $301,819.44 (2021), $298,353.78 (2020), and $300,263.70 (2019).

**What is the average price of 3-bedroom/3-bathroom homes for each year the home was built?**

The analysis found the average price of 3-bed, 3-bath homes is $292,676.79 (2017), $290,555.07 (2016), $288,770.30 (2015), $290,852.27 (2014), $295,962.27 (2013), $293,683.19 (2012), $291,117.47 (2011), and $292,859.62 (2010).

**What is the average price of a two-story, 3-bedroom/3-bathroom home with 2,000 square feet or more, for each year the home was built?**

The analysis found the average price of two-story, 3-bed/3-bath homes bigger than or equal to 2,000 square feet, is $280,317.58 (2017), $293,965.10 (2016), $297,609.97 (2015), $298,264.72 (2014), $303,676.79 (2013), $307,539.97 (2012), $276,553.81 (2011), and $285,010.22 (2010).

**What is the average price of homes with average prices greater than or equal to $350,000 per 'view' rating?** 

The full results for this query can be found in the code. The run times for each table are as follows:

- Original table: 0.5778 seconds
- Cached table: 0.5330 seconds
- Partitioned table: 0.0320 seconds

The cached table ran slightly faster than the original table, and the partitioned table ran far quicker than either of the others. Differences in runtime will be more significant with a larger dataset for home sales.

Note: all code blocks for runtime were run twice to eliminate the load time for the data.

## References
Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.
