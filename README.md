Guessing the missing youth unemployment data from China using a very quick and dirty linear regression model

After the youth unemployment (UE) rate (between 16-24 years old) reached a staggering 21.3% in Jun 2023, the highest in at least the past 3 years (earlier data was not checked), the Chinese government made the decision to discontinue the publication of such data from July 2023. However, other economic data continues to be regularly released, and it is reasonable to assume a close correlation among most economic indicators. This arouses my curiosity to explore whether it is possible to “guess” the missing July 2023 youth UE data using other available data. 

Interestingly, the government still publishes the “overall” UE rate, which stood at 5.3% in July 2023. They are clever enough not to disclose the “senior UE rate” (between 25 to 59 years old), as this enables us to deduce the youth UE rate by utilizing the “overall” and “senior” equivalent figures.

For my analysis, I sourced the data from the official government website (https://data.stats.gov.cn). To keep things simple for now, I focused on the data available on a monthly basis. This led me to a page containing 14 categories of data, ranging from “Price Index” to “Financial Intermediation”. After exercising some judgment, I downloaded 8 of these categories for further analysis. 
 
Each data file representing a category follows a similar format as below. It contains several data points, with a maximum download limit of 3 years, resulting in 35 data points excluding the July 2023 numbers of interest. I did some data cleansing such as removing the first 2 and the last row, filling in missing data with zero, etc. Additional, since many data points within each category exhibit high correlation, I selected one variable for analysis based on human judgment.
 
My objective was to conduct a regression analysis using the historical youth UE rate as the dependent variable (y-valye) and a set of parameters as the independent variables (x-value). The chosen variables comprised:
-	The Urban Surveyed Unemployment Rate
-	Value-added of Industry Growth Rate 
-	Investment Actually Completed in Fixed Assets Accumulated Growth Rate
-	Index of Service Production (ISP) Growth Rate 
-	Investment of Real Estate Accumulated Growth Rate
-	Total Retail Sales of Consumer Goods Growth Rate 
-	Total Value of Imports and Exports Growth Rate 
-	Comprehensive PMI output index

To perform the analysis, I utilized the Linear Regression model from the Sklearn library, enabling me to run the analysis with just two lines of code. The resulting R2 score, which indicates the model’s performance (with a maximum score of 1.0), was p.71. Considering the quick and rough nature of the analysis, this score is ok to me. 

Using the model’s generated results and incorporating the July 2023 data, the estimated youth UE rate is 18.8%. Surprisingly, this is lower than the previous month’s 21.3%, leading to questions about its accuracy. (Afterall, if the data trend is promising, why would the government cease its publication in the first place?) Nonetheless, I have no plans to refine the analysis at this stage. 

However, I did run the estimation over the past 3 years to compare it with the actual numbers. As shown below, the overall trend aligns closely with the actual figures, although some short-term deviations exist. 
 
That concludes this simple exercise. Here are some addition food for thoughts. 
1.	The analysis compares data points across the same time period. If the youth UE rate is indeed a leading indicator for some reason, the entire analysis may not be effective.
2.	How can empty data points be handled more effectively? Currently, I replaced them with zeros which is definitely not the best way.
3.	Apart from linear regression, which other models could potentially yield better results?
4.	Incorporating data available on a quarterly or annual basis may enhance the analysis. 
