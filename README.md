# Technical Product Manager (Current an MBA)
#### Technical Skills: Java, Python, SQL, AWS, Snowflake, and Figma

## Professional Experience
TikTok Product Manager @ Effects and Creation Team

![tiktok 3D effect engine](/assets/img/tiktok1.png)

![animation](/assets/img/ani2.gif) 
![animation](/assets/img/ani3.gif) 
![animation](/assets/img/ani4.gif)


## Machine Learning Project
### Abstract and Summary

In 2024 Fall, I enrolled in the Analytics in Action class at Columbia Business School. I worked with a real company in this class to solve its problems in a team of five. Electric is a Series D startup founded in 2016. The company provides comprehensive IT support to over 1,000 clients and handles over 44,000 monthly IT tickets. It spends around 1.32 million per month on human agents to solve these tickets. **Our project is to help Electric reduce this cost by designing a prediction model. The model will classify requests and determine whether they are automatable based on the first few messages. As a result, we designed a 2-option user interface mockup, reached an 80-90% accuracy range and saved $2 million annually.** 

### Current Situation: A Human-agent Chat-based System

Electric helps clients by solving their IT and security needs. Part of their help is about receiving tickets from email, website, and Slack. Most of the tickets are from Slack. User starts a direct message with a human agent. They solve the problem in the conversation. Electric handles 44,000 tickets monthly, costing them $1.3 million per month. While the existing human agents can handle tickets effectively, most of the tickets are repetitive and can be easily automated through classification models.

Our project is to help Electric reduce this code by designing a prediction model. The model will classify requests and determine they are automatable based on the first few messages.

![Slack conversation with a human agent](/assets/img/slack1.png)

### Key Data Challenges Before Building Models

The existing data set can not be easily analyzed because of certain challenges. 

**Challenge 1: Message Misalignment** The data contained entire conversations, many parts of which were irrelevant for initial category identification. We only need the first message for category prediction.

**Solution 1**  We focused solely on the initial user messages for immediate classification.


**Challenge 2: Too Many Ticket Categories** With over 200 categories, predicting outcomes became complex.

**Solution 2** We consolidated these into 8 key, actionable categories.

**Challenge 3: Data Imbalance** Some categories had significantly more examples than others.

**Solution 3** We used upsampling and downsampling techniques such as SMOTE to balance the dataset.

**Challenge 4: Overmasking** About 20% of messages were heavily masked, reducing their usability.

**Solution 4** We prioritized data with minimal masking and filtered out over-masked messages.

### Build Catagory Prediction Models
The category prediction model used Snowflake embedding and logistic regression, tree-based and neural network models.
1. Data Preparation: Snowflake’s multilingual-e5-large embedding converted text into numerical vectors, capturing semantic and contextual information.
2. Model Implementation: We tested five models: Logistic Regression, Random Forest, XGBoost, LightGBM, and Multilayer Perceptron (MLP). Our focus was on precision — minimizing false positives in automation classification.
The Results: LightGBM emerged as the top performer, achieving an 83% weighted average precision. Other models like XGBoost and Random Forest also delivered strong results, achieving approximately 82%.
A comparative analysis of model performance is illustrated in the chart below, highlighting LightGBM’s superior precision among the models.

![results for different models](/assets/img/a1.png)

### Refining Predictions: A Threshold-Based Approach
To further enhance accuracy, we implemented a threshold-based refinement for the LightGBM model. This involved selectively outputting one or two category predictions based on the model’s confidence level.

We explored two methods:
- Top Threshold: Outputting two predictions if the top-ranked prediction’s probability fell below a certain threshold.
- Gap Threshold: Outputting two predictions if the probability difference between the top two predictions was smaller than a threshold.

The Top Threshold method proved simpler and more effective, allowing us to balance accuracy with the number of predictions. We recommended a threshold range of 79%-98%, ensuring a 90%-95% chance of including the correct category while avoiding excessive two-prediction outputs.

![threhold](/assets/img/a2.png)

### Product Mockup from Threshold-based Approach

![High confidence: one option only](/assets/img/slack2.png)
![High confidence: one option only](/assets/img/slack3.png)

### Business Value
By automating 15.2% of Electric’s 44,000 monthly tickets (6,688 tickets), and assuming a $30 cost for manual handling and a 90% model precision, we project potential monthly savings of $180,576 and annual savings exceeding $2 million.

- Monthly Savings: 6,688 tickets x $30 per ticket x 90% precision = $180,576
- Yearly Savings: $180,576 x 12 = $2,166,912

### Future Suggestions and Final Thoughts
In the last half year, we worked with masked data. In the future, we would recommend Electric to
1. We suggest removing the asterisk and dealing with a cleaner version of the data
2. With the 90% accuracy of the current model, Electric could develop APIs for fully automated process
This project demonstrated how machine learning techniques can transform IT support. By automating repetitive and routine IT requests, Electric can significantly improve efficiency, reduce costs and empower the team to focus on more complex challenges.

### Reference 
[Link to Client Company>>](https://www.electric.ai/)
[Link to TikTok Effect House>>](https://effecthouse.tiktok.com/)



