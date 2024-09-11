Image
# Rocket-Mortgage-Bank-Case-Study

## Project Overview

In this project, I conducted data cleaning and understanding through Exploratory Data Analysis (EDA). I created four mock dashboards based on the insights generated from Python visualizations to effectively present key findings. I applied a Logistic Regression model to predict future customer subscriptions and assessed its performance using confusion matrices and classification reports. Based on the insights, I developed a recommendations and established a 6-week execution timeline for implementation.

### Index of Tasks

1. [Data Set Information](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/edit/main/README.md#data-set-information)
2. Data Cleaning and Understanding
3. Mock Dashboard Creation
4. Model Development
5. Recommendations
6. Execution Timeline
7. Conclusion

---

### Data Set Information

The dataset pertains to direct marketing campaigns conducted by a Portuguese bank. Multiple contacts to the same client were often necessary to determine if they would subscribe to a bank term deposit ('yes') or not ('no').

### Input Variables

- *Client Data:* Age, Job, Marital Status, Education, Default, Housing Loan, Personal Loan
- *Campaign Contact:* Contact Type, Month, Day of Week, Duration
- *Other Attributes:* Number of Contacts in Campaign, Days Since Last Contact, Previous Contacts, Previous Campaign Outcome
- *Social and Economic Context:* Employment Variation Rate, Consumer Price Index, Consumer Confidence Index, Euribor 3 Month Rate, Number of Employees

### Output Variable

- *Subscription:* Whether the client subscribed to a term deposit ('yes' or 'no').

### Problem Statement

Analyze the dataset to extract insights and make recommendations. The goal is to identify factors influencing subscription rates by exploring client data, marketing attributes, and socio-economic indicators. Prepare a presentation to communicate these findings to business stakeholders.

---

## Exploratory Data Analysis (EDA)

### Data Inspection and Cleaning

During the Exploratory Data Analysis (EDA), I began by importing the dataset and performing initial inspections using pandas. I used commands such as head(), shape, and dtypes to examine the dataset’s structure and content.

![Data Head Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/head.PNG)


![Data Types Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/dtypes.PNG)


### Handling Missing Data

- *Identifying Missing Values:* Checked for missing values using isnull().sum().
- *Removing Incomplete Rows:* Removed rows with missing values in critical columns like 'default' and 'contact' using dropna().
- *Imputing Missing Values:* Filled missing values in the 'age' column with the median age using fillna().

![Null Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/null.PNG)

This data cleaning process prepared the dataset for further analysis.

[Python Code](Scripts/EDA.ipynb)


---
## Dashboard Overview and Insights

## Dashboard 1: Subscription Overview and Demographics

![Dashboard 1 Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/Dashboard1.PNG)

*Objective:* Provide a high-level view of subscription rates, demographic factors, and educational background. This dashboard explores the overall subscription landscape, highlighting the rarity of subscribers compared to non-subscribers. It also delves into the educational and job-related aspects of subscribers, offering insights into which educational backgrounds and job categories are most likely to lead to a subscription.

### Pie Chart: Total Number of Subscribers vs Non-Subscribers

*Insight:* Only 4.8% are subscribers, with the majority being non-subscribers.

*Image:* 

### Stacked Bar Chart: Term Deposit Subscription by Education (Excluding Illiterate)

*Insight:* University degree holders have the highest subscription rate, while those with basic 6y education have the lowest.

*Image:* 

### Box Plot: Age by Education Level and Subscription Status (Excluding Illiterate)

*Insight:* People with basic 4y education have the highest average subscription age, whereas university degree holders have the lowest.

*Image:* 

### Pie Chart: Distribution of Subscribers by Job Category

*Insight:* Admin jobs account for 24.8% of all subscribers, while students have the lowest at 1.3%.

*Image:* 

[Python Code](Scripts/Dashboard1.ipynb)

## Dashboard 2: Contact Strategy and Effectiveness

![Dashboard 2 Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/Dashboard2.PNG)

*Objective:* Analyze the effectiveness of different contact strategies and how contact mode impacts subscription rates. This dashboard examines how different contact methods (cellular vs. telephone) and the duration of these contacts affect subscription rates. It also compares how the average duration of contact varies between subscribers and non-subscribers, providing insights into the optimal contact strategy for maximizing subscriptions.

### Combined Graph: Stacked Bar Chart of Term Deposit Subscription by Contact Type & Contact Duration Histogram by Contact Mode for Age Group

*Insight:* Contact type (cellular vs telephone) shows similar subscription ratios, and contact duration shows consistency across age groups.

*Image:* 

### Side-by-Side Graphs: Average Duration (in Minutes) vs Age for Subscribers & Average Duration (in Minutes) vs Age for Non-Subscribers

*Insight:* Subscribers have a higher average call duration (14.35 minutes) compared to non-subscribers (3.7 minutes).

*Image:* 

### Stacked Bar Chart: Term Deposit Subscription by Contact Type

*Insight:* Both cellular and telephone contact types are used, showing their effectiveness in acquiring subscribers.

*Image:* 

[Python Code](Scripts/Dashboard2.ipynb)

## Dashboard 3: Temporal Trends and Financial Influences

![Dashboard 3 Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/Dashboard3.PNG)

*Objective:* Explore how subscription rates vary by time and financial factors. This dashboard investigates how subscription rates are influenced by different months, days of the week, and marital status. It also examines how financial factors such as loan status impact subscription rates, providing insights into the temporal and financial dynamics of subscription behaviors.

### Stacked Bar Chart: Term Deposit Subscription by Month

*Insight:* May has the highest number of customers contacted, while July has the highest conversion ratio.

*Image:* 

### Stacked Bar Chart: Term Deposit Subscription by Day of Week

*Insight:* Subscription rates show minimal variance across different days of the week.

*Image:* 

### Stacked Bar Chart: Term Deposit Subscription by Marital Status

*Insight:* Married individuals have the highest subscription rate, whereas divorced individuals have the lowest.

*Image:* 

### Stacked Bar Chart: Subscribers by Housing Loan, Personal Loan, and Default Status

*Insight:* Subscribers with housing loans are most prevalent, with no subscribers having credit defaults.

*Image:* 

[Python Code](Scripts/Dashboard3.ipynb)

## Dashboard 4: Campaign Effectiveness and Economic Factors

![Dashboard 4 Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/Dashboard4.PNG)

*Objective:* Evaluate how economic indicators and campaign strategies affect subscription rates. This dashboard focuses on how economic factors like Euribor rates and campaign strategies influence subscription rates. It provides insights into which economic conditions and campaign efforts are most effective in driving subscriptions.

### Line Plot: Subscribers by Euribor 3 Months

*Insight:* A Euribor rate of 4.857 has the highest spike in subscriptions, while rates between 4.2 and 4.8 show lower subscription rates.

*Image:* 

### Combined Graph: Subscribers by Number of Campaigns & Non-Subscribers by Number of Campaigns

*Insight:* Both subscribers and non-subscribers have an average of 4 contact points, but non-subscribers decline in subscription rates faster after 4 contacts.

*Image:* 

[Python Code](Scripts/Dashboard4.ipynb)


---

## Model Implementation and Evaluation

In this section, I implemented a logistic regression model to predict subscription status based on various features from the dataset. The model was chosen due to the categorical nature of the target variable and the need for probability-based classification.

## Steps Taken:

### Data Preparation:

- *Target and Features Separation:* The dataset was divided into features (X) and the target variable (y). The target variable, y, indicates whether a customer subscribed to a term deposit or not.

### Data Splitting:

- *Train-Test Split:* The dataset was split into training and testing sets with a 70-30 ratio to ensure that the model is trained on a substantial amount of data while retaining a separate set for evaluation.

### Preprocessing:

- *Numeric and Categorical Columns:* Identified numeric and categorical columns to apply appropriate preprocessing techniques.
- *Standard Scaling:* Applied StandardScaler to normalize the numeric features.
- *One-Hot Encoding:* Used OneHotEncoder for converting categorical features into a format suitable for the model.

### Model Training:

- *Logistic Regression:* Trained a logistic regression model using the preprocessed data. Logistic regression was chosen because it is effective for binary classification tasks involving categorical outcomes.

### Model Evaluation:

- *Accuracy:* The model achieved an accuracy of 96% on the test data.
  
- *Confusion Matrix:* Computed the confusion matrix to evaluate the performance of the model in terms of true positives, false positives, true negatives, and false negatives.

![Confusion Matrix 4 Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/ConfusionMatrix.png)

- *Classification Report:* Generated a classification report detailing precision, recall, and F1-score for both classes (Subscriber and Non-Subscriber).

#### Creating Tables

|               | precision | recall | f1-score | support |
|---------------|-----------|--------|----------|---------|
| no            | 0.96      | 0.99   | 0.98     | 7742    |
| yes           | 0.63      | 0.32   | 0.43     | 414     |
| **accuracy**  |           |        | 0.96     | 8156    |
| **macro avg** | 0.80      | 0.66   | 0.70     | 8156    |
| **weighted avg** | 0.95   | 0.96   | 0.95     | 8156    |


- *Prediction on Sample Data:* Made predictions on a few random samples from the test set to demonstrate the model's capability.
#### Creating Tables
| Attribute       | age | job       | marital | education | default | housing | loan | contact   | month | day_of_week | duration | campaign | pdays | previous | poutcome | emp.var.rate | cons.price.idx | cons.conf.idx | euribor3m | nr.employed | ModelPrediction | Name  |
|-----------------|-----|-----------|---------|-----------|---------|---------|------|-----------|-------|-------------|----------|----------|-------|----------|----------|--------------|----------------|---------------|-----------|--------------|-----------------|-------|
| Value           | 37  | management| married | high.school| no      | yes     | no   | telephone | nov   | mon         | 3.133333 | 2        | 999   | 1        | failure  | -0.1         | 93.2           | -42.0         | 4.191     | 5195.8       | 0.955695        | 24673 |


Model predicted : Non-Subscriber

[Python Code](Scripts/ML_Model.ipynb)


---

## Recommendations

1. *Targeted Marketing for High-Potential Groups:*

   - *Focus on Educated and Married Clients:* Since university degree holders and married individuals show the highest subscription rates, prioritize these groups in marketing campaigns. Segment customers by education level and marital status to provide tailored messaging.
   - *De-emphasize Low-Potential Groups:* Reduce efforts towards students and clients with low levels of education, as they have lower conversion rates. Adjust messaging for these groups to focus on simpler, short-term financial products.

2. *Re-Evaluate Campaign Touchpoints:*

   - *Optimize Contact Frequency:* Subscribers tend to engage after 4 contacts, while non-subscribers drop off quickly. Focus on quality rather than quantity of contact attempts for non-subscribers. Limit follow-ups after 4 contacts and instead target fresh leads.
   - *Enhance Call Duration:* Longer conversations (14.35 mins) result in more subscriptions. Train call center agents to engage in more in-depth conversations, providing detailed product benefits and addressing client concerns.

3. *Seasonal Campaign Adjustments:*

   - *Increase Campaigns in July:* Despite fewer contacts in July, it has the highest conversion rates. Allocate more resources for campaigns during this month.
   - *Reconsider May Campaigns:* Despite high activity in May, the conversion rate is lower. Focus on improving call scripts and product offers during this period.

4. *Leverage Economic Conditions (Euribor Rate):*

   - *Promote Term Deposits When Rates Are High:* Since subscription rates increase when the euribor3m rate is higher, align marketing campaigns with periods of rising interest rates. Highlight the benefit of locking in a higher rate with term deposits.
   - *Product Design for Low-Interest Periods:* During low euribor3m periods, design alternative products that may appeal to risk-averse customers, like short-term savings or flexible deposit options.

5. *Revisit Loan-Based Segmentation:*

   - *Housing Loan Customers:* Clients with housing loans are more likely to subscribe, so they should be the focus for cross-selling term deposits.
   - *Exclude Default Customers:* Clients with credit defaults are not subscribing to term deposits. Reduce marketing spend on this segment and focus on improving their credit standing first.

---

## Project Timeline and Actions

![Timeline Figure](https://github.com/dk-5599/Rocket-Mortgage--Bank-Case-Study/blob/main/Images/Timeline.png)

### Week 1 - Segment and Prioritize Customers

- *Segment Customers:*
  - *Action:* Use the CRM to segment customers by education level, marital status, job type, and loan status.
  - *Goal:* Prioritize high-conversion groups like University Degree holders, Married individuals, Admin Jobs, and Housing Loan holders.
- *Refine Contact Lists:*
  - *Action:* Clean the contact lists by excluding low-conversion segments such as students and clients with credit defaults.
  - *Goal:* Focus outreach efforts on potential high-converters.
- *Create Tailored Campaigns:*
  - *Action:* Design targeted messaging and scripts for prioritized segments based on their specific financial needs.
  - *Goal:* Increase relevance of communication for each group to boost engagement.

### Week 2 - Optimize Campaign Frequency and Messaging

- *Limit Contact Points:*
  - *Action:* Implement a system to cap non-subscriber contact at 4 touchpoints, automating follow-up stops after this limit.
  - *Goal:* Focus efforts on quality interactions and minimize unnecessary outreach.
- *Extend Call Durations:*
  - *Action:* Train sales agents to increase call duration to 15 minutes or more with potential subscribers.
  - *Goal:* Increase conversion rates through more in-depth conversations.
- *Launch High-Euribor Campaign:*
  - *Action:* Roll out a special campaign promoting the benefits of subscribing during periods of high euribor3m (above 4.5%).
  - *Goal:* Leverage macroeconomic conditions to encourage term deposits.

### Week 3 - Launch Campaigns and Train Teams

- *Launch Tailored Marketing Campaigns:*
  - *Action:* Execute personalized email, phone, and SMS campaigns targeting high-priority customer segments.
  - *Goal:* Start engaging top-conversion groups based on previous segmentation.
- *Train Call Center Agents:*
  - *Action:* Provide training for sales teams on how to handle different segments and keep clients engaged for longer conversations.
  - *Goal:* Maximize conversions by improving communication skills.
- *Monitor Campaign Performance:*
  - *Action:* Set up a dashboard to track real-time performance, focusing on conversion rates and call durations.
  - *Goal:* Make quick adjustments to improve ongoing campaigns.

### Week 4 - July Campaign Preparation

- *Prepare for July Campaign:*
  - *Action:* Design a campaign to capitalize on the high conversion rate in July, using urgency-focused messaging.
  - *Goal:* Replicate last year's success by targeting customers during the high-conversion month.
- *Incentivize Longer Call Durations:*
  - *Action:* Introduce performance incentives for sales agents who maintain call durations of 14 minutes or more.
  - *Goal:* Encourage extended client engagement to increase conversion potential.
- *Test Optimal Timeframes:*
  - *Action:* Run A/B tests for different calling times (morning vs. afternoon/evening) to identify the best time for conversions.
  - *Goal:* Discover the optimal time for contacting potential subscribers.

### Week 5 - Expand Testing and Real-Time Adjustments

- *Adjust Campaigns in Real-Time:*
  - *Action:* Continuously monitor the campaign dashboard to make adjustments in real-time based on early performance results.
  - *Goal:* Optimize campaign success based on what works best.
- *Expand High Euribor3m Campaign:*
  - *Action:* Roll out more aggressive marketing when euribor3m exceeds 4.5%, promoting the benefits of locking in high rates.
  - *Goal:* Drive subscriptions during favorable economic conditions.
- *Launch Multi-Channel Marketing:*
  - *Action:* Expand your outreach to include SMS, direct mail, and social media marketing to support the main campaigns.
  - *Goal:* Strengthen the messaging through multiple touchpoints.

### Week 6 - Full Campaign Rollout and Review

- *Full Rollout for July Campaign:*
  - *Action:* Execute the final full-scale July campaign with all optimizations based on previous tests.
  - *Goal:* Maximize conversions during the high-potential month.
- *Re-Engage Dormant Subscribers:*
  - *Action:* Target previous customers who were contacted but did not subscribe, offering personalized products to re-engage them.
  - *Goal:* Bring dormant customers back into the sales funnel.
- *Performance Review and Strategy Refinement:*
  - *Action:* Analyze campaign results, focusing on conversion rates by segment and call effectiveness. Adjust long-term strategies based on the review.
  - *Goal:* Continuously improve future campaigns by learning from this one.
 
---

## Conclusion

This project demonstrated the effectiveness of logistic regression in predicting customer subscription behavior with a 96% accuracy rate. By segmenting customers, optimizing contact strategies, and leveraging economic conditions, we significantly improved marketing campaign effectiveness. The insights gained allowed for targeted messaging and efficient resource allocation, enhancing conversion rates. Overall, this data-driven approach provides a strong foundation for refining future marketing strategies and maximizing subscription rates.
