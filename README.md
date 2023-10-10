# **Data Analytics and Visualization Virtual Internship Experience - ACCENTURE**

⚙️ **Tool** : Excel <br>
💻 **Visualization** : Power BI <br>
🗂️ **Source Dataset** : Accenture


## 📂 **Overview**

Accenture is a leading global professional services company, providing a broad range of services and solutions in strategy, consulting, digital, technology, and operations. The intersection of business and technology have helped clients across a range of industries to improve their performance and create sustainable value for their stakeholders.

Under the Accenture Digital Solutions service, as a part of the Data Analytics team, we effectively analyze data sets to help Social Buzz, a large social media company, develop and optimize its content creation strategies.

To start our engagement with Social Buzz, we have embarked on a 3 month pilot with Social Buzz to focus on 2 main tasks.

<br>

---

## 📂 **Task 1 - Project Understanding**

### **Background Information**

Social Buzz needs help with its user’s data and due to their rapid growth and digital nature of their core product, the amount of data that they create, collect and must analyze is huge. They are still a small company and do not have the resources to manage the scale that they are currently at. The platform receives over 100,000 posts per day, of which, this is all unstructured data making it very hard to make sense of.

**Business Problem:**<br>

Client has reached a massive scale within recent years and limited resources to internally handle it.

**Business Objective:** 
- Audit of big data practice
- Analysis of popular content

The client provided Accenture with 3 datasets:
- Contents
- Reactions
- Reaction Types <br>
<br>

---

## 📂 **Task 2 - Data Cleaning & Modelling**

### **Background Information**

Social Buzz team is looking to boost business by analysing their existing user’s dataset to determine contents trends and popularity. Using the 3 existing datasets (Contents, Reactions and Reaction Types) as a labelled dataset, we will recommend which of these content categories should be targeted to drive the most value for the organization.

## **Data Cleaning**

### **Objectives**
- Remove rows with missing values and duplicates to ensure data integrity.
- Change the data type of specific columns, such as "Content Type," for consistency and analysis readiness.
- Eliminate irrelevant columns, like "URL" and "User ID," to focus on key variables for analysis.<br>

### **Result**

#### 1. Content Table

| Content ID                           | Content Type | Category       |
| ------------------------------------ | ------------ | -------------- |
| 97522e57-d9ab-4bd6-97bf-c24d952602d2 | Photo        | Studying       |
| 9f737e0a-3cdd-4d29-9d24-753f4e3be810 | Photo        | Healthy Eating |
| 230c4e4d-70c3-461d-b42c-ec09396efb3f | Photo        | Healthy Eating |
| 356fff80-da4d-4785-9f43-bc1261031dc6 | Photo        | Technology     |
| 01ab84dd-6364-4236-abbb-3f237db77180 | Video        | Food           |
| cf1e8c1a-23eb-4426-9f58-002fb1b53e91 | Gif          | Cooking        |

<br>

URL column is removed since it does not provide quantitative measurement of Category, which what we are looking to analyze. All missing values are removed and category duplicates are matched with each other to have a clean number of categories. Type column is specified with ‘Content Type’ to outline distinct analysis for our project. The result shows a clean data set of ‘Content ID’, ‘Content Type’ and ‘Category’.<br>
<br>

#### 2. Reaction Table

| Content ID                           | Reaction Type | Date       |
| ------------------------------------ | ------------- | ---------- |
| 97522e57-d9ab-4bd6-97bf-c24d952602d2 | Disgust       | 2020-11-07 |
| 97522e57-d9ab-4bd6-97bf-c24d952602d2 | Dislike       | 2021-06-17 |
| 97522e57-d9ab-4bd6-97bf-c24d952602d2 | Scared        | 2021-04-18 |

All missing values are removed from the rows to make sure every data line has an allocated ‘Reaction Type’. ‘User ID’ column is removed since it is irrelevant for our analysis since we analyze specifically for the content on which category have performing the best. The result shows a clean data set of ‘Content ID’, ‘Reaction Type’ and ‘Datetime’. Date is included to see when content is performing best and which specific category might be trending.  

## Data Modelling:

### Objectives
- **Data Integration:** Merge data from 3 tables to create a single, comprehensive dataset for analysis.
- **Top 5 Performing Category Analysis:** Analyze and identify the top 5 performing content categories within the dataset.  

### Result

#### 1. Data Integration: Merging 3 tables

| Content ID                           | Reaction Type | Date       | Content Type | Category | Sentiment | Score |
| ------------------------------------ | ------------- | ---------- | ------------ | -------- | --------- | ----- |
| 97522e57-d9ab-4bd6-97bf-c24d952602d2 | Disgust       | 2020-11-07 | Photo        | Studying | Negative  | 0     |
| 97522e57-d9ab-4bd6-97bf-c24d952602d2 | Dislike       | 2021-06-17 | Photo        | Studying | Negative  | 10    |
| 97522e57-d9ab-4bd6-97bf-c24d952602d2 | Scared        | 2021-04-18 | Photo        | Studying | Negative  | 15    |  

We use ‘Reaction’ table as our base table to join relevant columns from ‘Content’ and ‘Reaction Types’ data set using VLOOKUP function. This is done by common unique identifier (UID) that we use to integrate between the table data sets. ‘Content Type’ and ‘Category’ columns are merged in the base table with lookup value (Content ID) since it has the same UID across both spreadsheets. Next, ‘Sentiment’ and ‘Score’ columns are merged to determine the popularity of each content. Here, we are matching the ‘Reaction Type’ because it has a shared value with the base table.

#### 2. Aggregate Score 

| Category       | Aggregate Score |
| -------------- | --------------- |
| Animals        | 74965           |
| Science        | 71168           |
| Healthy Eating | 69339           |  

#### 2. Top 5 Categories by Aggregate Score 

| Category       | Aggregate "Popuarity" Score | Aggregate "Popuarity" Score |
| -------------- | --------------------------- | --------------------------- |
| Animals        | 74965                       | 21.36%                      |
| Science        | 71168                       | 20.28%                      |
| Healthy Eating | 69339                       | 19.76%                      |
| Technology     | 68738                       | 19.59%                      |
| Food           | 66676                       | 19.00%                      |  

Aggregate Score table is created by adding the cumulative score for the specific category to see its popularity. First, a discrete list of categories is created by removing the duplicates. We obtained 16 unique list of categories for our analysis. To add up the individual scores of each category, we use the SUMIF function to obtain the ‘Aggregate Score’. After sorting by descending, we obtained the Top 5 most popular categories.

---

## 📂 Task 3 - Data Visualization and Storytelling

### Background Information

After constructing the model, our next step involves presenting the results to our client. To effectively convey the insights we've derived, we employ visualizations that are clear, concise and engaging for our client.  
 
### Objectives
- Develop a dashboard
- Analyze the results and provide recommendations to clients.  

### Result

#### Top 5 Categories by Aggregate Score

<br>

<p align="center">
  <kbd><img width="400" src="https://github.com/nisa-g/VIX-Data-Analytics-Accenture/assets/139193734/89088340-83fd-47a8-ac2a-9bd1215d6b0f"></kbd> <br>
  Figure 1 — Top 5 Categories by Aggregate "Popularity" Score
</p>
<br>

Among the 16 unique content categories, the top 5 most popular categories of posts were animals, science, healthy eating, technology and food in descending order. Animals have taken the lead by a significant margin of an aggregate popularity score of around 74965 and Engagement Rate Reach (ERR) of 21.4%. It is very interesting to see both food and healthy eating within the top 5, it really shows that food is a highly engaging content category. Healthy eating ranks slightly higher than food, suggesting your user base may be skewed towards healthy eaters and health-conscious people. Finally, it is also interesting to see science and technology too. This may suggest that people enjoy consuming factual content and snippets of content that they can learn something from.

#### Popularity Percentage Share from Top 5 Categories

<br>

<p align="center">
  <kbd><img width="400" src="https://github.com/nisa-g/VIX-Data-Analytics-Accenture/assets/139193734/7938aba0-3468-48ec-a598-f81bbe14036c"></kbd> <br>
  Figure 2 — Popularity % Share from Top 5 Categories
</p>
<br>

Additionally, you can see from this chart the % split of popularity between the top 5 categories. There is not much difference between the share of each category, however, the difference between the 1st most popular, animals and the 2nd most popular, science, is the largest gap equal to 1.1%. In business terms, this could suggest that the most popular category, animals, is tailing away from the rest of the categories and may continue to get more and more popular. To avoid an issue where 1 content category consumes the entire platform, it will be important for you to ensure that any algorithms used to govern the content on the platform gives a fair balance to the content categories.

#### User Sentiment 

<br>

<p align="center">
  <kbd><img width="400" src="https://github.com/nisa-g/VIX-Data-Analytics-Accenture/assets/139193734/0edcc4a3-fd54-4000-9bc1-f1f2fa048c8c"></kbd> <br>
  Figure 3 — Users Sentiment by Score
</p>
<br>

Audio content leads with 83,170 points of positive engagements, closely followed by Photo content at 78,106 points, indicating the audience's strong interests for both audio and visual elements. However, Audio content also records the highest negative feedback at 6,112 points, while Photo content garners the lowest negative response at 5,754 points.

#### Content Posts by Month

<br>

<p align="center">
  <kbd><img width="400" src="https://github.com/nisa-g/VIX-Data-Analytics-Accenture/assets/139193734/bdbcdebb-1ac9-4cf7-ae59-501902e1b9bb"></kbd> <br>
  Figure 4 — Content Post by Month
</p>
<br>

January shows as the month of peak posting activity, boasting a substantial 2,218 posts, indicating a high level of user engagement during this period. In contrast, February experiences a notable dip in total posts, tallying at 1,980. This trend suggests that posting activity follows a distinctive undulating pattern in the number of posts from one month to another. The average post across the year shows 2,048 posts by average.

### Social Buzz Analytics Dashboard

<br>

<p align="center">
  <kbd><img width="900" src="https://github.com/nisa-g/VIX-Data-Analytics-Accenture/assets/139193734/28b51d80-a090-4ecf-b8eb-8bb667d13cac"></kbd> <br>
</p>

<br>

## Recommendations

1. Animals and science are the two most popular categories, suggesting that users like "real-life" and "factual" content.

2. Food was a common theme amongst popular content and the most popular food category was healthy eating. This could be a signal to show the types of people that are using your platform, and you could use this insight to boost engagement even further. For example, you could run a campaign with content focused on this category or work with healthy eating brands to promote content.

3. Given the increasing influence of technology, there is no surprise to witness technology-related content ranking prominently among the top categories. This clearly demonstrates users' enthusiasm for tech-related content. A promising strategy could involve partnering with renowned tech industry leaders, which has the potential to significantly boost user engagement to new heights.

4. Given the high positive engagement with audio content, continue exploring popular audio trends, such as podcasts or voice-based interactions, to keep the audience engaged. Host live Q&A sessions or discussions related to audio content to encourage audience participation and feedback.

5.	Encourage users to share their own photos related to the content, using captions and narratives to enhance their user experience and creating a sense of community and involvement.

6.	As much as this analysis was insightful, we are ready to take it to the next stage and we have the expertise within Accenture to help you realize these kinds of insights in production across your organization and in real-time.


