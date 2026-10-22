# Capstone-Project--E-commerce-Sales-and-Review-Analysis
 ABSTRACT

The project “E-Commerce Sales and Review Analysis” focuses on analysing clothing e-commerce data using Python to identify sales patterns, customer feedback trends, product performance, and return behaviour. 
The analysis involves data cleaning, handling missing values, correcting inconsistent entries, and identifying outliers while preserving genuine data values. Exploratory Data Analysis (EDA) is performed and they are used to create meaningful visualizations. These visualizations help examine product price distributions, category-wise sales, seasonal sales patterns, customer ratings, review counts, and return rates. 
The primary objective of this project is to transform raw e-commerce data into meaningful business insights that can support better inventory planning, product assortment decisions, pricing strategies, and customer satisfaction initiatives. Overall, the project demonstrates how Python-based data analysis and visualization can help e-commerce businesses understand product performance, identify potential improvement areas, and make data-driven business decisions.

INTRODUCTION 
E-commerce has become an important part of the modern retail industry, allowing businesses to reach customers through online platforms and offer a wide variety of products. With the growth of online shopping, analysing sales data and customer feedback has become essential for understanding customer preferences, monitoring product performance, and improving business strategies.
The project “E-Commerce Sales and Review Analysis” focuses on analysing clothing e-commerce data using Python. The study aims to understand sales patterns, product performance, customer reviews, and return behaviour to identify useful insights from the available data. It also examines how sales vary across product categories and seasons, helping to understand differences in product performance.
Python libraries such as Pandas and NumPy are used for data processing and analysis, while Matplotlib, Seaborn supports data visualization. The analysis helps identify trends, relationships, and potential areas for improvement in inventory management, pricing decisions, and customer satisfaction.
Overall, this project demonstrates the importance of data analytics in e-commerce and how meaningful insights from historical data can support better business decisions and contribute to improved operational efficiency.

 Problem Statement
In the competitive e-commerce industry, understanding sales performance, customer feedback, and product return patterns is essential for making effective business decisions. However, raw sales and review data may contain missing values, inconsistencies, and outliers, making it difficult to identify meaningful patterns and trends.
The main problem addressed by this project is the lack of clear insights into product performance, seasonal sales variations, customer ratings, and return behaviour. Without proper analysis, businesses may face challenges in inventory planning, pricing decisions, product selection, and improving customer satisfaction.
Therefore, this project aims to clean and analyse the clothing e-commerce dataset using Python, investigate relationships between sales and other numerical variables, compare product performance across categories and seasons, and examine customer ratings and return patterns.

Project Objectives
•	To perform data cleaning and preprocessing by handling missing values, duplicate records, inconsistent entries, and potential outliers.
•	To analyse clothing sales performance across different product categories and seasons.
•	To evaluate product prices, discount percentages, and units sold to understand sales patterns.
•	To analyse customer ratings and review counts to understand product popularity and customer feedback.
•	To examine product return rates and identify potential areas for improving customer satisfaction.
•	To investigate relationships among numerical variables to identify patterns associated with sales performance and customer reviews.
•	To identify key business insights and provide recommendations for improving inventory management, pricing strategies, product assortment, and overall business performance.

DATASET DESCRIPTION
The dataset is obtained from Kaggle and it contains 5,001 records and 16 columns related to women's e-commerce clothing products, customer reviews, and sales performance.
The following table describes the purpose of each column in the dataset.
Sl. No.	Column Name	Description
1	product_id	A unique identifier assigned to each clothing product.
2	OrderDate	The date associated with the product order, used to analyse sales trends over time.
3	category	The main category to which a clothing product belongs, such as Dresses, Tops, or Jeans.
4	subcategory	The specific type of clothing within a main category, such as Skinny Jeans or V-Neck T-Shirt.
5	material	The fabric or material used to manufacture the clothing product, such as Cotton or Denim.
6	color	The colour of the clothing product, such as Black, Red, or Blue.
7	size	The available size of the clothing product, such as S, M, L, or XL.
8	season	The season for which the product is intended, such as Summer, Winter, Spring, or Fall.
9	style	The style or fashion category of the product, such as Casual or Business Casual.
10	price_usd	The original product price expressed in US dollars.
11	discount_percent	The percentage discount applied to the product price.
12	rating	The customer rating given to a product, indicating the level of customer satisfaction.
13	review_count	The number of customer reviews associated with a product.
14	stock_quantity	The quantity of the product currently available in stock.
15	units_sold	The total number of units sold for a product.
16	return_rate	The proportion or percentage of sold products that are returned by customers, according to the dataset's definition.
Tools and Technologies
1. Python: Python is the primary programming language used for data analysis and manipulation.
2. Google Colab: Google Colab is a cloud-based platform used to write and execute Python code without requiring local software installation.
3. Pandas: Pandas is used to load, clean, organize, and manipulate the dataset, including handling missing values and removing duplicate records.
4. NumPy: NumPy is used for numerical computations and mathematical operations during data analysis.
5. Matplotlib: Matplotlib is used to create visualizations such as bar charts, histograms, line charts, scatter plots, and box plots.
6. Seaborn: Seaborn is used to create statistical visualizations, including count plots, box plots, and correlation heatmaps, to identify patterns and relationships in the dataset.
7. Plotly: Plotly is used to create interactive visualizations that help explore sales trends and product performance.

DATA LOADING AND INITIAL INSPECTION
The dataset is loaded into the Google Colab environment using the Pandas library. Initial inspection is performed to understand the structure, size, column names, data types, and overall characteristics of the dataset before proceeding with data cleaning and preprocessing.

import pandas as pd
 df=pd.read_csv("/content/E commerce Sales and Review Analysis.csv")

The head() and tail() functions are used to display the first five and last five records, respectively. The shape attribute identifies the total number of rows and columns, while columns displays the names of all columns in the dataset. The dtypes attribute identifies the data type of each column, and the info() function provides a concise summary of the dataset, including non-null values and memory usage. Finally, the describe() function generates descriptive statistical information about numerical columns, including count, mean, standard deviation, minimum, maximum, and quartile values.
These inspection techniques provide an initial understanding of the dataset and help determine the necessary steps for data cleaning and further analysis.

DATA CLEANING AND PREPROCESSING
Data cleaning and preprocessing are essential steps in preparing the dataset for accurate and reliable analysis. In this project, the clothing e-commerce dataset is examined to identify and correct data quality issues before performing Exploratory Data Analysis (EDA).
The preprocessing stage includes:
1.	Handling Missing Values
The dataset was checked for missing values using the isnull().sum() function in Pandas. The inspection identified missing values in eight columns: 
Subcategory(1), material(2), size(10), season(4), rating(3), review_count(6), stock_quantity(1), and units_sold(2). The remaining columns contained no missing values.
In total, 29 missing values were identified across eight columns. The size column contained the highest number of missing values, with 10 records, followed by review_count with 6 records.
•	For categorical columns such as subcategory, material, size, and season, the missing values are replaced with the mode (the most frequently occurring value).
•	For numerical columns such as rating, review_count, stock_quantity, and units_sold, the missing values are replaced with the median to reduce the influence of extreme values. 

2. Removing duplicate records
Duplicate records are identified using the df.duplicated().sum() function to determine whether the dataset contains any repeated rows and the result showed that the dataset contained 1 duplicate record.
The duplicate record was removed using the df.drop_duplicates() function to avoid redundant data. After removing the duplicate, the dataset was verified again using df.duplicated().sum(), which returned 0, confirming that no duplicate records remained.
The dataset initially contained 5,001 records and 16 columns. After removing one duplicate record, it contained 5,000 records and 16 columns. Verification confirmed that no duplicate records remained.
3.Correcting data types
The data types of the dataset columns were inspected using df.dtypes. The OrderDate column was stored as an object data type, so it needs to be converted to datetime format to support time-based analysis.
Some numerical columns representing counts, such as review_count, stock_quantity, and units_sold, were stored as float64. These columns can be converted to integer data types because they represent whole-number counts.
Correcting the data types improves data consistency and allows the columns to be used appropriately for calculations, grouping, and visualization.
4.Identifying and handling outliers using the IQR method
The Interquartile Range (IQR) method is used to identify potential outliers in the numerical columns of the clothing e-commerce dataset. Outliers are values that fall significantly below or above the typical range of the data. Identifying these values helps assess unusual observations and determine whether they require correction or should be retained for analysis.
The IQR method uses the first quartile (Q1) and third quartile (Q3) to calculate the range of the middle 50% of the data.
•	Q1 (First Quartile): The value below which 25% of the observations fall.
•	Q3 (Third Quartile): The value below which 75% of the observations fall.
•	IQR: The difference between Q3 and Q1
The formulas used are:
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    Lower_limit = Q1 - 1.5 * IQR
    Upper_limit = Q3 + 1.5 * IQR

1. Price (price_usd)
The IQR method identified 125 outliers in the price_usd column, with an upper limit of approximately $149.60. Higher prices may represent premium clothing products, so these values were considered potentially genuine. Therefore, the identified outliers were retained without capping to preserve the actual price distribution.
2. Discount Percentage (discount_percent)
The IQR method identified 254 outliers above the upper limit of 37.5%. Since clothing discounts can legitimately range from 0% to 50%, these values may represent valid promotional offers. Therefore, no outlier capping was performed, and the observed values were retained for analysis.
3. Review Count (review_count)
The IQR method identified 509 outliers above the upper limit of 20 reviews. Products with a higher number of reviews may indicate greater customer engagement or popularity. Since these values can provide useful business insights, they were retained without capping, provided they were valid observations.
4. Stock Quantity (stock_quantity)
The IQR method identified 234 outliers above the upper limit of 121.5 units. Higher stock quantities may reflect bulk inventory maintained for popular products or seasonal demand. Therefore, the identified outliers were retained without capping, provided the quantities were valid and non-negative.
5. Return Rate (return_rate)
The IQR method identified 44 outliers above the upper limit of 0.205 (20.5%). The highest observed return rate was approximately 0.23 (23%), which is only slightly above the statistical limit. These values may represent genuine product return patterns and could help identify products with higher return rates. Therefore, the values were retained for further analysis.
             The IQR method identifies statistical outliers, not necessarily incorrect data. If an extreme value is genuine, retaining it is often more appropriate than replacing it with the median.

5. Handling incorrect data
All numerical columns were examined to identify incorrect or invalid values. During this process, two negative stock quantity values were identified in the stock_quantity column. Since stock quantity represents the number of units available in inventory, negative values are considered invalid. Therefore, these values were replaced with 0 to maintain data accuracy and consistency.

6.Correcting inconsistencies in categorical columns
The value_counts() method was used to examine each categorical column and identify inconsistencies, such as:
•	Spelling mistakes
•	Different spellings for the same category
•	Unexpected category values
•	Inconsistent capitalization
During this process, an incorrect value, "Causal", was identified in the style column. It was a spelling mistake for "Casual" and was corrected to maintain consistency in the dataset.
This correction ensures that the style column contains consistent category names for accurate analysis and visualization.

After completing the data cleaning and preprocessing steps, the dataset was verified to ensure that the necessary corrections had been applied successfully and that the dataset was consistent and ready for Exploratory Data Analysis.

Exploratory Data Analysis (EDA)

1.Understanding Individual Columns
Exploratory Data Analysis (EDA) was performed on the cleaned and pre-processed clothing e-commerce dataset to understand the characteristics of individual columns. Both numerical and categorical variables were analysed to identify the distribution of data, common values, and important patterns within the dataset.
2. Analysis of Numerical Data
Descriptive statistical analysis was performed on the numerical columns using measures such as mean, median, minimum, maximum, and standard deviation. These statistical measures help understand the average values, central tendency, range, and variability of the data.
The analysis provides an overview of important numerical attributes, including product prices, discount percentages, customer ratings, review counts, stock quantities, units sold, and return rates. These measures help identify variations in product characteristics and support further analysis of sales performance, inventory levels, and customer reviews.
3. Analysis of Categorical Data
The categorical columns were analysed using frequency counts to understand the distribution of products across different categories and characteristics. The value_counts() method was used to identify the most frequently occurring values in each categorical column.
The analysis revealed the following findings:
•	Product Category: Dresses were the most frequently occurring product category.
•	Subcategory: V-Neck T-Shirt was the most common subcategory.
•	Material: Cotton was the most frequently occurring material.
•	Color: Black was the most common product color.
•	Size: Medium (M) was the most frequently occurring size.
•	Season: Summer was the most common season associated with the products.
•	Style: Casual was the most frequently occurring product style.
These findings provide an overview of the dominant product characteristics in the clothing e-commerce dataset. Understanding the frequency distribution of these attributes helps describe the product assortment and provides a foundation for further analysis of product categories, customer preferences, sales performance, and inventory management.

Data Visualization
Data visualization was performed on the cleaned clothing e-commerce dataset to identify patterns, trends, and relationships among product attributes, sales performance, customer reviews, inventory levels, and return rates. Various charts were created using Python libraries such as Matplotlib, Seaborn, and Plotly.
The visualizations help transform numerical and categorical data into graphical representations, making it easier to understand the dataset and derive meaningful business insights.

1.Univariate Analysis
1.1Product price distribution
Graph type: Histogram
Variables used: price_usd
A histogram was created to examine the distribution of product prices in the clothing e-commerce dataset. It shows how frequently products fall within different price ranges. Most products are priced between approximately $20 and $80, with the highest concentration around $30–$40. As the price increases, the number of products generally decreases.
 
1.2Distribution of Units Sold per Product
The box plot illustrates the distribution of units sold across products in the clothing e-commerce dataset. The distribution is highly right-skewed, indicating that most products have relatively low sales quantities, while a small number of products have exceptionally high sales. The highest sales value exceeds 10,000 units.

1.3Product Distribution across various Seasons
Graph type: Count plot
Variable used: season
A count plot was created to analyse the number of product records associated with each season. It provides a comparison of the seasonal distribution of clothing products in the dataset.
The categorical analysis identified Summer as the most frequently occurring season. 
 

2. Bivariate Analysis
2.1 Product price vs units sold
Graph type: Scatter plot
The scatter plot illustrates the relationship between product prices and units sold in the clothing e-commerce dataset. A strong concentration of high-volume sales is observed at lower price points. The majority of high-performing products, with sales exceeding 4,000 units, are priced below $50.As product prices increase, the number of units sold generally decreases
 

2.2 Units sold across product categories
Graph type: Scatter plot
The scatter plot illustrates the distribution of units sold across different product categories in the clothing e-commerce dataset. Most product categories show a similar baseline distribution, with sales volumes heavily concentrated below 2,000 units. However, Dresses exhibit the highest sales spikes, reaching nearly 10,000 units. In comparison, Jumpsuits and Coats generally show lower sales volumes than other categories.
 

2.3 Average return rate by material
The bar plot compares the average return rate of clothing products across different materials. Nylon has the lowest average return rate, indicating comparatively fewer product returns among items made from this material. Leather and wool also show relatively low average return rates. In contrast, Denim has the highest average return rate among all the materials analysed.
 
2.4 Average rating by clothing style
The bar plot compares the average customer ratings across different clothing styles. Overall, the average ratings for all styles are approximately 3.0, indicating a similar level of customer satisfaction across most styles. However, Streetwear has a comparatively lower average rating, while Formal clothing has the highest average rating among the styles analysed.

         
2.5 Discount percentage vs. units sold
The scatter plot illustrates the relationship between discount percentage and units sold in the clothing e-commerce dataset. The visualization does not show a strong positive relationship between higher discounts and increased sales volume. Most sales remain concentrated within a similar range across different discount levels, suggesting that increasing discounts does not necessarily lead to a substantial increase in units sold. Notably, the highest sales volume occurs at a 0% discount, indicating that some high-demand products can achieve substantial sales without promotional discounts.


2.6 Product category by season
The visualization compares product categories across different seasons to identify seasonal sales patterns. T-shirts in Summer represent the highest-volume product category, highlighting strong demand for lightweight clothing during warmer months. Sweaters and Coats in Winter also stand out, recording relatively high sales volumes during the colder season. In contrast, everyday clothing categories such as Jeans, Loungewear, and Activewear show more consistent sales across seasons, suggesting relatively stable demand throughout the year.
 

3.Multivariate Analysis
3.1 Correlation heatmap: Numerical variables
The correlation heatmap illustrates the strength and direction of linear relationships between the numerical variables in the clothing e-commerce dataset. The strongest relationship is a strong positive correlation between review_count and units_sold (0.91), indicating that products with more customer reviews tend to have higher sales volumes.
A weak positive correlation between rating and review_count (0.21) is also observed, suggesting a slight tendency for products with more reviews to have higher ratings. 

3.2 Seasonal sales by category
The visualization compares sales performance across product categories and seasons, highlighting differences in seasonal demand. Activewear achieves its highest sales during Summer, performing exceptionally well compared with other seasons. Dresses show strong sales across multiple seasons, particularly All Season, Summer, and Winter, indicating demand throughout the year. Sweaters record their highest sales during Winter, while Jackets perform well in both Autumn and Winter. Other categories show lower sales during
certain seasons, suggesting that purchasing patterns vary according to product type and seasonal requirements.
 

Line Chart- Monthly Sales Trend
The line chart illustrates the monthly sales trend from January 2024 to July 2026. Sales fluctuate throughout the period, with several peaks and declines. The highest sales levels occur between August and October 2025, indicating a period of strong sales performance. However, sales decrease significantly in early 2026, suggesting a weakening sales trend in the later part of the period.
 
Pie Chart- Product Distribution by Category

  
The pie chart illustrates the distribution of clothing products across different product categories in the dataset. Dresses account for the largest share of products, followed by Tops and Jeans. In contrast, Sets and Jumpsuits contribute the smallest shares to the overall product distribution. This indicates that the product catalogue contains a greater proportion of Dresses, Tops, and Jeans compared with these smaller categories.

Key Findings and Insights
1. Product Pricing and Sales: Most products are priced between $20 and $80, with high-volume sales concentrated mainly among products priced below $50.
2. Product Categories: Dresses have the highest product representation and show exceptional sales peaks, while Jumpsuits and Coats generally have lower sales volumes.
3. Customer Reviews: A strong positive correlation of 0.91 exists between review count and units sold, indicating that products with more reviews tend to have higher sales.
4. Discount Impact: Higher discounts do not necessarily result in increased sales. Some products achieve high sales volumes without discounts.
5. Seasonal Demand: T-shirts and Activewear perform well during Summer, while Sweaters and Jackets show stronger demand during colder seasons.
6. Customer Ratings: Average ratings are around 3.0 across clothing styles, with Formal clothing rated comparatively higher and Streetwear lower.
7. Return Rates: Nylon has the lowest average return rate, while Denim has the highest, indicating a need to investigate possible reasons for Denim product returns.
8. Monthly Sales Trend: Sales peak between August and October 2025, followed by a significant decline in early 2026.
9. Product Distribution: Dresses contribute the largest share of products, followed by Tops and Jeans, while Sets and Jumpsuits have smaller shares.

RECOMMENDATIONS
•	Pricing Strategy: Maintain competitive prices for popular products and evaluate pricing strategies for premium products.
•	Inventory Management: Ensure sufficient stock for high-demand products and adjust inventory according to seasonal sales patterns.
•	Customer Engagement: Encourage genuine customer reviews and use customer feedback to improve product quality and customer satisfaction.
•	Discount Optimisation: Apply targeted discounts to slow-moving products rather than unnecessarily reducing prices on high-demand products.
•	Return Rate Reduction: Investigate the high return rates of Denim products and improve sizing information, product descriptions, and quality checks.
•	Product Improvement: Analyse lower customer ratings for Streetwear products to identify areas for improvement.
•	Sales Monitoring: Track monthly sales trends to identify declining performance and develop suitable promotional strategies.

CONCLUSION
The project, E-Commerce Sales and Review Analysis, explored clothing product data to identify patterns in pricing, sales performance, customer ratings, return rates, and seasonal demand. Using Python libraries such as Pandas, NumPy, Matplotlib, Seaborn, and Plotly, the dataset was cleaned, processed, analysed, and visualised to extract meaningful business insights.
The analysis revealed important relationships between customer reviews and sales, differences in seasonal demand, and variations in product return rates. The findings also highlighted opportunities to improve pricing strategies, inventory management, customer satisfaction, and promotional activities.
Overall, this project demonstrates how data analysis and visualisation can support informed business decisions and help clothing e-commerce businesses improve operational efficiency and sales performance.

LIMITATIONS
•	The analysis is limited to the available clothing e-commerce dataset and its recorded attributes.
•	Customer behaviour and purchasing decisions cannot be fully understood using product-level data alone.
•	The dataset may not capture external factors such as competitor pricing, market trends, and changing customer preferences.
•	Limited Customer Information: The dataset does not contain detailed customer demographics or individual purchase histories, limiting customer-level behavioural analysis.




Future Scope

•	Inventory Optimisation: Develop a system to estimate stock requirements and reduce overstocking and stock shortages.
•	Customer Sentiment Analysis: Analyse customer reviews to identify satisfaction levels and common product complaints.
•	Return Prediction: Build predictive models to identify products that may have a higher probability of being returned.
•	Profitability Analysis: Incorporate product costs, operational expenses, and marketing  expenditure to analyse profit margins.
•	 Interactive Dashboard: Develop a Power BI dashboard to monitor sales, product performance, seasonal trends, and return rates.

REFERENCES

Dataset Source: https://www.google.com/url?q=https%3A%2F%2Fwww.kaggle.com%2Fdatasets%2Frazanihababdellatif%2Fwomens-e-commerce-clothing-reviews-and-sales
Plotly Python Documentation: https://plotly.com/python/getting-started/ 
Google Colab:  https://colab.research.google.com/

