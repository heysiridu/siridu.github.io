# Technical Product Manager
**Technical Skills** Java, Python, SQL, AWS, Snowflake, and Figma<br>
**Brief Self-intro** I am an MBA student at Columbia Business School and expect to graduate in Spring 2025. I am taking a series of Computer Science classes at Columbia Engineering. Before my MBA, I was a product manager at TikTok, building a 3D effect engine and working with the machine learning algorithm to allocate traffic on TikTok. I also worked in a series C product-led growth designer collaboration platform and led the AI functions roadmap.

## Professional Experience
### TikTok Product Manager @ Effects and Creation Team
- Led product planning and design for 3D effect engine at TikTok, in alignment with company-level revenue and profits goals
- Spearheaded the 3D effect engine's usage growth and promotion effort, increasing browsing rate by 62%

<p float="left">
  <img src="assets/img/tiktok1.png" alt="TikTok 3D effect engine" width="600">
</p>

- Visual Showcases for some of the most popular effects

<p float="left">
  <img src="assets/img/ani2.gif" alt="Animation 1" width="180">
  <img src="assets/img/ani3.gif" alt="Animation 2" width="180">
  <img src="assets/img/ani4.gif" alt="Animation 3" width="180">
</p>

---

## Machine Learning Project for a Series D Startup
### Abstract and Summary

In 2024 Fall, I enrolled in the Analytics in Action class at Columbia Business School. I worked with a real company in this class to solve its problems in a team of five. Electric is a Series D startup founded in 2016. The company provides comprehensive IT support to over 1,000 clients and handles over 44,000 monthly IT tickets. It spends around 1.32 million per month on human agents to solve these tickets. **Our project is to help Electric reduce this cost by designing a prediction model. The model will classify requests and determine whether they are automatable based on the first few messages. As a result, we designed a 2-option user interface mockup, reached an 80-90% accuracy range and saved $2 million annually.**

### Current Situation: A Human-agent Chat-based System
<p align="center">
  <img src="assets/img/slack1.png" alt="Slack conversation with a human agent" width="600">
</p>

Electric helps clients by solving their IT and security needs. Part of their help is about receiving tickets from email, website, and Slack. Most of the tickets are from Slack. User starts a direct message with a human agent. They solve the problem in the conversation. Electric handles 44,000 tickets monthly, costing them $1.3 million per month. While the existing human agents can handle tickets effectively, most of the tickets are repetitive and can be easily automated through classification models.

Our project is to help Electric reduce this cost by designing a prediction model. The model will classify requests and determine they are automatable based on the first few messages.

### Key Data Challenges Before Building Models

- **Challenge 1** Message Misalignment
  The data contained entire conversations, many parts of which were irrelevant for initial category identification. We only need the first message for category prediction.  
- **Solution**: We focused solely on the initial user messages for immediate classification.

- **Challenge 2** Too Many Ticket Categories  
  With over 200 categories, predicting outcomes became complex.  
- **Solution**: We consolidated these into 8 key, actionable categories.

- **Challenge 3** Data Imbalance  
  Some categories had significantly more examples than others.  
- **Solution**: We used upsampling and downsampling techniques such as SMOTE to balance the dataset.

- **Challenge 4** Overmasking
  About 20% of messages were heavily masked, reducing their usability.  
- **Solution**: We prioritized data with minimal masking and filtered out over-masked messages.

### Build Category Prediction Models

The category prediction model used Snowflake embedding and logistic regression, tree-based, and neural network models.

1. **Data Preparation**: Snowflake’s multilingual-e5-large embedding converted text into numerical vectors, capturing semantic and contextual information.  
2. **Model Implementation**: We tested five models:
   - Logistic Regression
   - Random Forest
   - XGBoost
   - LightGBM
   - Multilayer Perceptron (MLP)

   Our focus was on precision — minimizing false positives in automation classification.  
3. **Results**: LightGBM emerged as the top performer, achieving an 83% weighted average precision. Other models like XGBoost and Random Forest also delivered strong results, achieving approximately 82%.

<p align="center">
  <img src="assets/img/a1.png" alt="Results for different models" width="500">
</p>

### Refining Predictions: A Threshold-Based Approach

To further enhance accuracy, we implemented a threshold-based refinement for the LightGBM model. This involved selectively outputting one or two category predictions based on the model’s confidence level.

- **Top Threshold**: Outputting two predictions if the top-ranked prediction’s probability fell below a certain threshold.
  
- **Gap Threshold**: Outputting two predictions if the probability difference between the top two predictions was smaller than a threshold.

Recommendation: A threshold range of 79%-98% to ensure 90%-95% correct category inclusion while avoiding excessive two-prediction outputs.

<p align="center">
  <img src="assets/img/a2.png" alt="Threshold analysis" width="600">
</p>

### Product Mockup from Threshold-based Approach
To demonstrate how the threshold-based model works in reality, we build several product mockups: 
- Scenario 1: when the prediction model is highly confident about one option, it produces only one result. For example, “Add John Doe to the Electric IT Support channel in Slack” resulted in a single, confident prediction. If none of them satisfy the options, the "CANCEL" button directs the user to human agents.
<p align="center">
  <img src="assets/img/slack2.png" alt="High confidence: one option only" width="600">
</p> 

- Scenario 2: when the model is less confident about prediction results, it outputs two options. A more ambiguous request like "Add her on Slack to the engineering team" resulted in two options: “Add to Engineering Channel” and “Add to ML/AI Group,” giving the user more freedom to pick. If none of them satisfy the options, the "CANCEL" button directs the user to human agents.

<p align="center">
  <img src="assets/img/slack3.png" alt="High confidence: two option" width="600">
</p>   


### Business Value
By automating 15.2% of Electric’s 44,000 monthly tickets (6,688 tickets), and assuming a $30 cost for manual handling and a 90% model precision, we project potential monthly savings of $180,576 and annual savings exceeding $2 million.

- **Monthly Savings**: 6,688 tickets x $30 per ticket x 90% precision = $180,576  
- **Yearly Savings**: $180,576 x 12 = $2,166,912  

### Future Suggestions and Final Thoughts

1. Suggest removing the asterisks and cleaning the dataset for better performance.  
2. With the 90% accuracy of the current model, Electric could develop APIs for fully automated processes.  

This project demonstrated how machine learning techniques can transform IT support. By automating repetitive and routine IT requests, Electric can significantly improve efficiency, reduce costs, and empower the team to focus on more complex challenges.

---

### References
- [Link to Electric.ai >>](https://www.electric.ai/)  
- [Link to TikTok Effect House >>](https://effecthouse.tiktok.com/)
