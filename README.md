# Health Insurance Cross-Selling
### Using Machine Learning to rank a list of customers most likely to buy a Car Insurance for a cross-sell campaign.

![alt_text](https://github.com/igorvgp/DS-health-insurance-cross-sell/blob/main/media/health-insurance.jpg) 

## 1. Abstract

This Data Science Project was inspired by this [kaggle Challenge](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction) and presents the development of a Classification Machine Learning Model, more specifically a Learning to Rank Model, used to generate a propensity score to purchase a new product for a company's customer list.

<p align="justify">An Insurance company that has provided Health Insurance to its customers need to predict whether the policyholders (customers) from past year will also be interested in Car Insurance provided by the company.
With the information about customers, the company did a survey asking them if they were interested in car insurance. With the results of this survey and the characteristics of the customers, the company is able to maximize profit through Machine Learning techniques can identify customers with a greater propensity to purchase a new insurance, since they company only have the resourses to call 20,000 customers.</p>

<p align="justify">The solution was delivered through a "Get Prediction" button on Google Sheets that returns the purchase propensity of each customer on the list. Thus, sellers can target customers who have the highest chance of purchasing insurance.</p>

A demo of the solution can be seen in the gif below:


<img src="media/sample_video.gif" width="800">

<p align="justify">Compared to a random selection of customers to be contacted, the machine learning model developed proved to be about 3 times more efficient, generating an extra gain of 35 million dollars.</p>

## 2. Methodology

<p align="justify">To develop this project, the CRISP-DM methodology was used, aiming at delivering the solution efficiently, and evolving at each cycle.</p>

<img src="media/CRISP-DM.png" width="800">

To direct your reading, below are links to the development carried out at each stage of the CRISP cycle:

* [Business Understanding](https://https://github.com/igorvgp/DS-health-insurance-cross-sell## 3. Business Undestanding)
* [Data Understanding](https://https://github.com/igorvgp/DS-health-insurance-cross-sell## 4. Data Understanding)
* [Data Preparation](https://github.com/vitorhmf/cross-sell#5-data-preparation)
* [Machine Learning Modeling](https://github.com/vitorhmf/cross-sell#6-machine-learning-modeling)
* [Evaluation](https://github.com/vitorhmf/cross-sell#7-evaluation)
* [Depoyment](https://github.com/vitorhmf/cross-sell#8-deployment)

## 3. Business Undestanding

### 3.1. Context

<p align="justify">The CEO of a Health Insurance company wants to expand the business by offering Car Insurance. The company carried out a customer survey in which they had to answer whether they would buy car insurance from the company. 381109 customers answered the survey and the results were saved in the database along with other customer attributes.</p>

<p align="justify">Now, the company is ready to launch the new service, and the sales team have a list of 127,000 customers to make phone calls and offer the new Insurance. Considering that the sales team has the capacity to make 20,000 calls within the campaign period, the goal is to build a solution that ranks the customers most likely to buy the new service.</p>

<p align="justify">The features of the database are described below:</p>

| Feature                | Definition                                                                                               |
|------------------------|----------------------------------------------------------------------------------------------------------|
| id                     | Unique ID for the customer                                                                               |
| gender                 | Gender of the customer                                                                                   |
| age                    | Age of the customer                                                                                      |
| driving_license        | 0 : Customer does not have DL, 1 : Customer already has DL                                               |
| region_code            | Unique code for the region of the customer                                                               |
| previously_insured     | 1 : Customer already has Vehicle Insurance, 0 : Customer doesn't have Vehicle Insurance                  |
| vehicle_age            | Age of the Vehicle                                                                                       |
| vehicle_damage         | 1 : Customer got his/her vehicle damaged in the past. 0 : Customer didn't get his/her vehicle damaged in the past. |
| anual_pemium           | The amount customer needs to pay as premium in the year                                                  |
| policysaleschannel     | Anonymized Code for the channel of outreaching to the customer ie. Different Agents, Over Mail, Over Phone, In Person, etc. |
| vintage                | Number of Days, Customer has been associated with the company                                            |
| response               | 1 : Customer is interested, 0 : Customer is not interested                                               |


*Source:* [Kaggle](https://www.kaggle.com/datasets/anmolkumar/health-insurance-cross-sell-prediction)


### 3.2. Business Assumptions

	1. Customers who already have Health Insurance may also be interested in Auto Insurance.
	
	2. Cross-selling increases customer loyalty.
	
	3. Learning from cross-selling can become a horizontal strategy for the company in the market.
	
	4. A machine learning model to rank customers most likely to buy will increase sales force productivity and accelerate new market entry.
	

## 4. Data Understanding

### 4.1. Main Insights

##### Hypothesis 1: Customers with new cars are more interested in insurance

Result: False

<img src="media/responsesxvehicle-age.png" width="600">

Customers with older vehicles are more likely to buy car insurance.
 
##### Hypothesis 2. Older people are more interested in auto insurance

Result: True

<img src="media/responsesxage.png" width="800">

Customers between 33 and 52 years represent 58% of the interested group.

##### Hypothesis 3. Vehicles that are already insured have lower damage rate

Result: True

<img src="media/pr-insxdamage.png" width="600">

Vehicles that was previously insured have low damage rate.

##### Hypothesis 4. customers with new cars are more likely to have car insurance

Result: True

<img src="media/agexpr-ins.png" width="600">

Most of the new cars are already insured, thats why the hypotesis 1 (Customers with new cars are more interested in insurance) is false.

# 5 - Machine Learning Model

![alt_text](cross_sell/reports/figures/gain_curve.png) 

The Logistic Regression model was selected for presenting the best performance of the tested algorithms.

X-Axis: Number of customers

Y-Axis: Algorithm's ability to sort by customers likely to buy

# 6 - Machine Learning Performance

Ranking Position: 2000 

Recall: 0.08 

Precison: 0.32

# 7 - Business Result

### 1. Main Insights on the most relevant attributes of customers interested in purchasing auto insurance.

- Customers with new cars are more likely to take out insurance.
- 58% of the positive response are between 33 and 52 years old
- 76% of customers who had damaged cars responded positively.
- Men represent the most positive responses.

### 2. What percentage of customers interested in purchasing auto insurance will the sales team be able to contact by making 20,000 calls?

- With 20.000 calls sales team will be contact 61% of customers interested

### 3. If the sales team capacity increases to 40,000 calls, what percentage of customers interested in purchasing auto insurance will the sales team be able to contact?

- With 40.000 calls sales team will be contact 99% of customers interested

### 4. How many calls does the sales team need to make to contact 80% of customers interested in purchasing auto insurance?

- With 27.500 calls sales team will be contact 80% of customers interested

# 8 - Deploy


![alt_text](cross_sell/reports/figures/sheets.gif) 

The API with the ranking model is available to the company and can be accessed by Google Sheets, the sales team can provide the customer information to get the ranking score.

# 9 - Lessons Learned

The problem of learning to rank requires other metrics to assess the performance of the algorithm, these metrics are adapted from classification models.

# 10 - Next Steps to Improve

In this solution, classes were not balanced in model training. Another tool is the application of hyperparameters to improve algorithm performance and cross-validation to ensure that the algorithm evaluation is not biased.


