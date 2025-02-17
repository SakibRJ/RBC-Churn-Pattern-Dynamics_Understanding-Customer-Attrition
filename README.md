# Royal Bank of Canada Churn Pattern Dynamics: Understanding Customer Attrition

## Description 

Churn prevention is vital for companies across various industries, as retaining existing customers is typically more cost-effective than acquiring new ones. In this case, we have a dataset from the Royal Bank of Canada (RBC), with attributes outlined in the Business Requirements Document (BRD). Churn refers to customers who stop using a company’s product or service, and understanding the factors driving this behavior is key to enhancing retention strategies. By analyzing churn data, RBC can identify patterns, develop targeted loyalty programs, and design effective retention campaigns to reduce the likelihood of customers leaving.

Churn prevention is not a one-size-fits-all approach. It requires a deep understanding of customer behavior and a tailored strategy for retention. By analyzing churn data, RBC can gain valuable insights into the root causes of customer loss and implement specific actions to address these issues. Offering personalized loyalty programs, improving customer service, and addressing customer pain points are all effective ways to boost retention and ensure long-term business success.

### Approach
1. Understanding the data and planning accordingly. (More on this refer BRD)

2. Data cleaning/wrangling: Cleaning and preparing the data: Like any other data this data was in the raw format, various steps have been taken to clean this dataset (Tech stack used: Excel). Some of them involve using statistical descriptive values like median to replace blanks in the 'Estimated Salary' attribute, removal of blanks, mode value to replace 'Tenure' attribute, removal of duplicate rows etc.

3. Insights: Analysing the data to extract meaningful insights: Here churn analysis is done with EDA approach including Univariate, bivariate analysis on exit customers.

4. Visualizing key factors for clear and concise communication: The 'RCB_Churn_Analysis.pibx' file includes a dashboard along with a multi-page analysis of trends and patterns, highlighting key takeaways, which helps RBC understand their customers better and track events wrt churn.

5. Drawing conclusions with key highlights of data patterns and trends, complemented by actionable insights and a comprehensive report summary on the final page.


### Steps followed after cleaning the data in EXCEL

- Step 1 : Load data into Power BI Desktop from multiple sources, dataset is in a .csv and .xlsx format files.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present since I managed to clean the dataset in the Excel prior to importing.
- Step 5 : In the report view, a simple tri-coloured custom theme was selected.
- Step 6 : A master calender table was constructed for errorless and smooth operations of DAX functions/Measures
- step 7 : Later, started with Power Pivot and Modelling establishing the connections by managing the relationships (More on this in the .pbix file 'model view' tab)
- step 8: Multiple DAX expression were written under a newly established table 'My_Measures' for easy access and to extract meaningful insights including Total customers, Active members, Inactive members, Credit card holders, Non-Credit card holders, retained customers, exit customers, churn % etc...
- Step 8 : Key Visual filters (Slicers) were added for important filter fields namly "Year", "Financial quarter", "Location". This basically helps the user to play along with the data as per the requirements within the Homepage/Dashboard.

Snap of the Homepage/Dashboard (Power BI DESKTOP) is pasted below for reference:

![Image](https://github.com/user-attachments/assets/3839068d-d112-4418-8deb-dae070ccc749)

- Step 9 : A new column 'CreditScoreRemark' was added in the 'Bank_churn' table to analyse data based on credit scores of the customers.
           
        CreditScoreRemark = SWITCH(
        true(),
        Bank_Churn[CreditScore] >= 800 && Bank_Churn[CreditScore] <= 850, "Excellent", 
        Bank_Churn[CreditScore] >= 740 && Bank_Churn[CreditScore] <= 799, "Very Good",
        Bank_Churn[CreditScore] >= 670 && Bank_Churn[CreditScore] <= 739, "Good",
        Bank_Churn[CreditScore] >= 580 && Bank_Churn[CreditScore] <= 669, "Fair",
        Bank_Churn[CreditScore] >= 300 && Bank_Churn[CreditScore] <= 579, "Poor"
        )
Snap of new calculated column ,

![Image](https://github.com/user-attachments/assets/86496771-4a36-4b2b-835d-cb22ff17dd62)

- Step 10 : Time intelligence measure was added to track exit customers by month and previous month.
        
        Prev Month Exit Customers = CALCULATE([Exit Customers],DATEADD(MasterCalender[Date], -1, MONTH))


Snap of the line graph Visual for 'Exit customer vs Prev Month Exit Customers'

![Image](https://github.com/user-attachments/assets/b10a024f-e58a-409e-aafb-1b2499163f74)

- Step 11 : A series of visualizations and pages were created to effectively illustrate key data trends and insights. Additionally, for some of these visuals, the report includes a section highlighting the 'key takeaways', ensuring a clear understanding of the findings. For a more detailed and in-depth analysis, please refer to the accompanying .pbix file, which contains additional insights and interactive elements."

- Step 12 : Finally, the last page of the report provides a comprehensive summary, encapsulating the key findings and detailed patterns identified throughout the analysis. This section highlights the most significant insights related to customer churn, offering a clear overview of the underlying factors. In addition to summarizing the findings, the page also presents some of actionable recommendations and strategic suggestions aimed at reducing churn within RBC’s customer base, helping to enhance customer retention and long-term business growth.
       

#### A single-page homepage/dashboard report is created using Power BI Desktop, providing a high-level overview of key metrics and trends. This dashboard serves as the starting point for the analysis, offering a clear snapshot of the most important data points. Following this, multiple pages of detailed analysis were developed, each focusing on specific aspects of the churn data ensuring easy interpretation of the findings.

#### At the end of the report, a dedicated Insights/Summary page consolidates the most critical findings from the analysis, offering a comprehensive summary of the data trends, key patterns, and potential areas of concern related to customer churn. This page also includes actionable insights and some of strategic recommendations aimed at addressing churn and improving customer retention. For a deeper exploration of the churn analysis, please refer to the .pbix file, which provides access to interactive visualizations and further detailed insights.
