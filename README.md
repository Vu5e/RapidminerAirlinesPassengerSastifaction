# Prediction on Airlines Passenger Sastifaction

## Business Understanding
- Passenger Satisfaction – Customer Retention and Loyalty.
- Customer satisfaction is a metric of how services offered by the airline company meet customer expectations.
- Customers’ satisfaction plays a major role in retaining the customers.
- Evaluation of customer satisfaction is one good factor that helps in decision making strategy.
- Adopting suitable strategy  will results in increasing loyalty  which generates customers’ satisfaction.

## Analytical Question
- Satisfaction is the result of somebody who defined feeling pleased or dissatisfied by the outcome of comparing the perceived quality of the company with the anticipated quality of a product or services (Ismail, 2012).
- It is from this fact the airline started to offer various incentives, brochures, competitive prices, and computerized reservation system with purpose of creating customer loyalty (Ismail, 2012). 
- Airline firms across the globe are being eviscerated by Covid-19, as most international flights traffic has been grounded. However, after the hurricane is over, demand for air travel is predicted to boost as people hurry back to overseas vacations (Alvin T. P., 2020). 
- Airlines can gain the competitive edge by creating a classification model to identify the crucial components that lead to customer satisfaction. 
- In this study, the model chosen is Decision Tree, Naïve Bayes and Random Tree.

## Objectives
- To construct suitable model to predict customer satisfaction of airlines services.
- To determine the performance of the Decision Tree, Random Tree and Naive Bayes in predicting customer satisfaction of airlines services.

## Data Description
- Data Source - Kaggle
- This dataset contains an airline passenger satisfaction survey.
- This data contain 23 attributes with 129880 observations.

![image](https://user-images.githubusercontent.com/28688869/139123979-a321720e-839f-4744-b46a-9b238d595392.png)

## Data Understading
### List of Features

![image](https://user-images.githubusercontent.com/28688869/139124053-9579ede8-4560-4e10-a0bd-b4e514242054.png)

### Passenger Sastifaction
- 56,428 passenger satisfied with the airlines services provided.
- However, the other 73,452 passenger do not satisfied with airlines services.

![image](https://user-images.githubusercontent.com/28688869/139124132-3d01d551-8b7d-44b0-a98c-27c3bf0eb20f.png)

## Data Preparation
### What kind of preparation?
- Join tables between two datasets.

![image](https://user-images.githubusercontent.com/28688869/139124252-8cc70faa-2e7e-4628-ba94-581ceaa07425.png)

- Highly correlated features are more linear and thus have nearly the same effect on the dependent variable.
- There is high (positive) correlation between Departure Delay in Minutes and Arrival Delay in Minutes (0.965) and also ease online booking and inflight wifi service (0.715) 

![image](https://user-images.githubusercontent.com/28688869/139124314-0b0d8cfa-58b6-4c33-a5d8-67ab780085b4.png)

- Using “Select Attributes” operator.
- Excluded features
  - “att1”
  - “Departure Delay in Minutes”
  - “Ease of Online Booking”
  - “id”
- Attribute Filter Type Parameter will be “subset”.

![image](https://user-images.githubusercontent.com/28688869/139124407-cd410977-54cb-4431-9163-391014921ce5.png)

- Replacing features name.
- Using “Replace” Operator to replace features name.
- Attribute filter type will be “subset”.
- Chosen features will be “satisfaction”.
- Replacing features name of “satisfied” to “Yes”.

![image](https://user-images.githubusercontent.com/28688869/139124473-1208be17-2a8e-4231-aaf5-e7b2dfa74945.png)

- Replacing features name.
- Using “Replace” Operator to replace features name.
- Attribute filter type will be “subset”.
- Chosen features will be “satisfaction”.
- Replacing features name of “neutral or disYes” to “No”.

![image](https://user-images.githubusercontent.com/28688869/139124534-3ba29507-aad2-4a21-b1c3-4c0b9d47b534.png)

- Using the “Rename” operator to rename the label.
- Renaming from old name “satisfaction” to “satisfied”.

![image](https://user-images.githubusercontent.com/28688869/139124594-a54f5bee-782c-4e31-aca9-5795f849ff7e.png)

- Setting the roles.
- Using the “Set Role” operator to set the roles.
- In the “Parameter”, attribute name “satisfied” will be chosen and target role will be “label”.

![image](https://user-images.githubusercontent.com/28688869/139124661-8482848a-4f8b-40f1-9a1f-8de8954dc298.png)

## Modelling
### Cross Validation
- The Cross Validation Operator is a Nested Operator with two subprocesses: a Training subprocess and a Testing subprocess. 
- The Training subprocess is used for training a model. In the Testing subprocess, the trained model is then applied. 
- The performance of the model is measured during the Testing phase.

### Decision Tree
![image](https://user-images.githubusercontent.com/28688869/139124841-4bcb83f8-a7a9-4aa4-8238-4d8cb0e23152.png)

### Naive Bayes
![image](https://user-images.githubusercontent.com/28688869/139124899-4edbec9f-561e-4bec-a992-7cd940897996.png)

### Random Tree
![image](https://user-images.githubusercontent.com/28688869/139124935-78d495e0-c167-4aca-87a8-3e06186c6d58.png)

## Evaluation
### ROC Curve
- Area under the ROC curve is a measure of model performance.
- Decision Tree has the best performance compared to Random Tree and Naive Bayes.

![image](https://user-images.githubusercontent.com/28688869/139125029-6ae99129-5ccd-4d3b-80b0-98b2307c4150.png)

### Accuracy & Precision
- Recall or sensitivity gives us information about a model’s performance on false negatives (incorrect prediction of passengers who are satisfied).
- Precision gives us information of the model’s performance on false positives.
    - In this case, we may be far more concerned about having low false positives (low precision) than false negatives (recall).
    - What do we do with predicted not-satisfied passengers?
      - Improving the services offered e.g. easier check in service and baggage handling.
      - Offering special package which includes wifi and hotel discounts.

![image](https://user-images.githubusercontent.com/28688869/139125145-4d9cc6a0-ad8e-4dee-a1e9-fe82d59f5c4f.png)

### Feature Importance
- Feature importance was obtained from the Decision Tree’s weights output port.
- A weight is given by the sum of improvements the selection of a given Attribute provided at a node.
- The amount of improvement is dependent on the Information Gain obtained.

![image](https://user-images.githubusercontent.com/28688869/139125227-9918aa33-7094-438f-bd8e-364193602ee7.png)

- Important features include Inflight wifi service (1) and Customer Type (2).
- Feature importance indicates how useful the Attributes are in predicting the target variable.

- Feature importance can provide insight into the model.
  - The weights obtained will highlight which are the most relevant features to the target.
  - In many real world applications of predictive modeling, the user is interested in finding out features that are key “drivers” or “triggers” that are likely to affect the outcome (or the target).
  - Feature importance provides a driver to control the optimization of some objective in a business problem.
- Therefore, Inflight wifi service influence the customer’s satisfaction the most, followed by Customer Type (loyal or disloyal) and Flight Distance.
- Pricing Strategy for wifi - current price seems costly and prevents many passengers from connecting to the Internet.
  - Airlines should reconsider the pricing strategy in order to be competitive and attract other general passengers in the future.
  - For example:
    - Free wifi for one hour - for passengers of long journey
    - Less data cap for wifi
    - Cheaper for long journey
    - Business traveller - unlimited additional data

### Inflight WiFI Service
- The barchart shows satisfaction level of the inflight wifi service.
- Based on the barchart, it can be conclude that the closer the satisfaction level of the inflight wifi service to the scale of 5, the greater the number people who are satisfied with airlines services.

![image](https://user-images.githubusercontent.com/28688869/139125507-fba6c752-787e-4af7-ac90-62c91439d9b5.png)
