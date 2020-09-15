# IBM-Employee-Attrition

Attrition, in Human Resource terminology, refers to the phenomenon of the employees leaving the company. Attrition in a company is usually measured with a metric called attrition rate, which simply measures the no of employees moving out of the company (voluntary resigning or laid off by the company). Attrition Rate is also referred as churn rate or turnover. An organization is only as good as its best employees. In an ever-changing economy, it is getting harder and harder to retain best employees. You might be able to offer respectable wages, perks and a great working environment but there will be several other factors that come into play.
You're probably using cutting edge tech and big budgets to make sure your Sales, Marketing, Development, etc. are up to par with industry standards, so why is Human Resources being ignored? Although the cost doesn't appear to be too apparent over financial quarters, there are quite a few hidden costs that accumulate.
Here are just some of the ways in which employee churn can affect a company:
1.	Team Productivity: Having valuable employees leave can have a major impact on your team morale. This can lead to increased responsibilities for other team members eventually leading to longer hours and team dissatisfaction. If the company culture tends to be bad, this coupled with other factors can also lead to more turnover within your team or department.
2.	Recruitment: If you're working in a team with a heavy workload and tough schedule, chances are you would need a replacement as soon as possible. This would most definitely cost you and depending on how skilled you want your staff; this can be quiet time intensive.
3.	Training: This is standard protocol for most companies, training your new employees is crucial. If you happen to hire an employee for a skilled position, you'll probably end up spending quite a bit of time and money training your new hire.
These are just some of the ways in which you could be losing money with your lost employees. This may not seem like a lot but at the end of the day this is an additive issue and if money and time aren't an issue for company, this can also create a bad public image for any company and its employees.
Data Description:
The dataset has 35 columns and 1470 entries. The dataset includes both nominal and interval data. Attrition is the label in our dataset and would like to find out why employees are leaving the organization. 1237 (84% of cases) employees did not leave the organization while 237 (16% of cases) did leave the IBM organization making our dataset to be considered imbalanced since more people stay in the organization than they actually leave.
 
Data Cleaning & Preparation:
In the real world however, most of the time, Data will be presented in all sorts of forms and conditions. Being able to effectively clean, combine and prepare data will set up for success whenever striving to build a model. As this dataset is from Kaggle, dataset is relatively clean, any cleaning done is mainly to improve quality of life for coding. Columns such as education that are numerical that actually represent categorical variables may need further investigation. EmployeeCount is a constant column with all values being 1. Performance rating whilst being on a scale of 1-4, only has 3s and 4s. Standard Hours is a constant column with all values being 80 hours. I have dropped the two constant columns such as 'EmployeeCount','EmployeeNumber'. I have also ordered the values of education by ranking below_college as 1 and till  Doctor as 5.

Exploratory Data Analysis:
Attrition in business describes a gradual but deliberate reduction in staff numbers that occurs as employees retire or resign and are not replaced. The term is also sometimes used to describe the loss of customers or clients as they mature beyond a product or company's target market without being replaced by a younger generation. From EDA of the dataset there are numerous things that stand out in relation to attrition.
Class imbalance
Class imbalance in the target variable can be problematic when it comes to modelling, and in relation to this dataset focus is the minority class. Class imbalance creates a high baseline accuracy for our models to improve on. Methods to reduce this imbalance may be needed such as under/oversampling.
 Attrition & Age
Attrition seems to be more prevalent in the early career stages, most notably between the ages of 20 and 30. Whilst there is records of attrition at almost every age grouping, it would be beneficial to retain these younger employees and develop them within the business.

 


Attrition & Monthly income
While it isn't ground-breaking that the employees getting paid more are less likely to quit their jobs, exploring this area did uncover certain job roles where despite their pay level, attrition was abnormally higher than other roles. This relationship between income and retention could also be worth exploring in relation to preventing attrition, by offering incentives in the form of pay increases, how much of an effect, if any, would this have on the employee’s attrition chance.
 Attrition & overtime
Employees that worked overtime had a much higher rate of attrition than their colleagues that didn’t have to. By increasing the total number of hours worked and making workers stay late/arrive early the chance of them leaving increases. Again, this provides another potential area of focus to improve employee retention, by minimising overtime hours, employee satisfaction could increase, and the chance of attrition could go down for this specific group of employees.
 

Attrition & Job role
Showing the average monthly income per job role on top of the attrition count per job role unveils an interesting relationship with the highest paid jobs averaging the lowest attrition and vice versa. Jobs such as Sales executive however go against this trend with a higher average income whilst recording the second highest attrition rate out of all the job roles.
Predictive Modelling:
Post the EDA, I have understand the significant factors influencing the attrition variable, I will be building suitable data models which should be able to truly represent the relationship between the variables of our interest and also help us in answering the business questions that I am looking answers for. In this project, I’ll be using predictive modelling capabilities and see if I can predict employee attrition on this synthetically generated IBM dataset. I will be building predictive model with decision tree and then build with other supervised learning models to predict employee attrition.
Decision Tree
Classification is a more complex data mining technique that forces you to collect various attributes together into discernible categories, which you can then use to draw further conclusions, or serve some function. Decision tree is a type of supervised learning algorithm that can be used in both regression and classification problems. It works for both categorical and continuous input and output variables. A decision tree is a decision support tool that uses a tree-like graph or model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility. It is one way to display an algorithm.

 
Developing a training model using rpart function and plotting the Decision Tree it is evident that people who are working overtime and those who are paid less salary have higher chance of leaving the company. After plotting the decision tree, I applied the decision tree model on training data set and got an accuracy of 89.39% 
Training Dataset:				 Validation Dataset:
                              
And then to predict the accuracy of model obtained from decision tree calculation, I applied the model on validation data set and got an accuracy of 82.72%. Accuracy is less compared to accuracy obtained when I applied to model on training data set. This is expected has the model was created from training data set and is supposed to have higher accuracy. The accuracy of validation data set after applying the decision tree is as below.                                              
ROC Curve
 
AUC
 
From the above figure it’s concise that there is high chance of Attrition for new Attrition follows the Decision tree as below:
TotalWorkingTime >=4 AND OverTime =No AND MonthlyIncome >=3995 AND TotalWorkingTime  >= 6
Random Forest
Since the decision trees suffers from high variance, meaning if you split the training data into 2 parts at random, and fit a decision tree to both halves, the results that you get could be quite different. Random Forests is a versatile data mining method capable of performing both regression and classification tasks. It uses bagging and feature randomness when building each individual tree to try to create an uncorrelated forest of trees whose prediction by committee is more accurate than that of any individual tree. The output below illustrates applying a random forest in R to the dataset. I also observed a improvement in the accuracy to 84.9% when model was applied on validation data frame.
Validation Dataset:
                                                    
However, random forests can produce “variable importance” scores, which measure the relative contribution of the different predictors. The importance score for a particular predictor is computed by summing up the decrease in the Gini index for that predictor over all the trees in the forest. Below figure shows the variable importance plots generated from the random forest model for the dataset. From the below it’s clear that Overtime, TotalWorkingYears, age and Monthly income are the variables with high scores, play important role in the attrition of a company.
Variable Importance Plot 
Logistic Regression
Logistic regression is a statistical analysis method used to predict a data value based on prior observations of a data set. Logistic regression has become an important tool in the discipline of data mining. The approach allows an algorithm being used in a data mining application to classify incoming data based on historical data. As more relevant data comes in, the algorithm should get better at predicting classifications within data sets. A logistic regression model predicts a dependent data variable by analyzing the relationship between one or more existing independent variables. 
In the data set using the glm() function I calculated the coefficient for every attribute. Positive coefficients for the dummy variables mean that they are associated with higher probabilities of Attrition. I obtained an accuracy of 90.48% and 85.03% on training and validation dataset respectively.
 

 








Training set:                                                              Validation dataset:

                                                                                                                   
The ROC curve and area under the curve of logistic regression model is as below. Area under the curve was found to be greater than decision tree model. 

                     
I also predicted the first 10 values of validation dataset from model built on training dataset.  The attrition probability greater than 0.5 was considered to be Yes(1) and probability less than 0.5 was considered to No(0). Table below consists of actual and predicted values for validation data set.
             
Neural networks
Neural networks, also called artificial neural networks, are models for classification and prediction. The neural network is based on a model of biological activity in the brain, where neurons are interconnected and learn from experience. Neural networks mimic the way that human experts learn. The learning and memory properties of neural networks resemble the properties of human learning and memory, and they also have a capacity to generalize from particulars.
From the variable importance plot obtained from random forest model, I used top 7 variables to create the neural network model and obtained the below network using neuralnet package.

         

The weights and node bias of above neural network model is as below:
 
Naive Bayes
Naive Bayes is a simple, yet effective and commonly used, machine learning classifier. It is a probabilistic classifier that makes classifications using the Maximum A Posteriori decision rule in a Bayesian setting. It can also be represented using a very simple Bayesian network. Naive Bayes classifiers have been especially popular for text classification and are a traditional solution for problems such as spam detection.  The only work that must be done before prediction is finding the parameters for the features’ individual probability distributions, which can typically be done quickly and deterministically. This means that Naive Bayes classifiers can perform well even with high-dimensional data points and/or a large number of data points.
A-priori probabilities and Conditional probabilities of Attrition in IBM employee dataset is as below. From the below result we can infer that, if the Education of employee is increased by one unit from college to Bachelor there will be increase by 19.77% chances of Attrition of employee. In the same manner, Attrition can be calculated for other variables using the below conditional probability of Naïve bayes model.
 
The accuracy of model on training dataset and validation dataset was 85.4% and 84.1% respectively.
Training Dataset:                                                       Validation Dataset:
                  

Support Vector Machine
A Support Vector Machine (SVM) is a discriminative classifier formally defined by a separating hyperplane. In other words, given labelled training data (supervised learning), the algorithm outputs an optimal hyperplane which categorizes new examples. In two-dimensional space this hyperplane is a line dividing a plane in two parts where in each class lay in either side. Our objective is to find a plane that has the maximum margin, i.e the maximum distance between data points of both classes. Maximizing the margin distance provides some reinforcement so that future data points can be classified with more confidence.
I obtained 389 support vectors when I applied “Radial” SVM kernel for modelling. SVM when model when applied on training data set and validation dataset, got an accuracy of 86.7% and 83%
  
     

Conclusion:
Every organization should calculate the attrition rate because a high attrition rate indicates an organizational problem. While some companies with large bodies of frontline workers see high attrition as simply par for the course, a high attrition rate can almost always be boiled down to internal problems and issues. Given the high cost of staff turnover, honesty really does pay off for the job candidate and the organization. The best way to avoid these types of situations is to be honest with the information included in the description for the position, such as the shift the employees will be working, what advancement opportunities will be available and when, and how much flexibility employees will have.
From variable importance plot I got to know that the top 5 factors that influence the attrition seem to be:
•	Overtime
•	Monthly income
•	Job level
•	Age
•	Number of companies worked before
•The main general reason behind attrition is most likely the effort-reward imbalance. In this case, this mostly applies to people who are working overtime and who in many cases have a relatively low salary. It should be checked whether there is an effective overtime policy in our company to reduce overtime.
• Our simple decision tree shows that further solutions may not lie uniquely in people getting higher salaries (or their overtime pay). Those with relatively higher salaries may be interested in something more than just a paycheck, and might still leave if they do not feel part of the company (e.g. if they don't have any stock options, or if they don't have access to trainings);
• I have also found that different facets of work-life balance might represent an issue for employees (a finding supported by visualizations). One of the things that should be checked is whether there is a lack of certain teleworking arrangements in our company;
• Job role with highest probability of attrition is sales representative. Something should be definitely done about that to retain sales representative within the company. This could be done by raising salary, providing more benefits and reducing overtime.
Last but not least, if we would be given a new dataset of our employees, we could calculate probabilities and see which employees exactly are prone to leaving - with an algorithm that outperformed standard algorithms (e.g. Random Forest)!
Attrition isn't an entirely unavoidable problem, but it can certainly be addressed as early as the hiring process and by organizing HR audit for each of above areas, just to see what can be improved or what is lacking.


References:

1.	https://www.kaggle.com/pavansubhasht/ibm-hr-analytics-attrition-dataset
2.	https://datasciencebeginners.com/2018/12/20/multinomial-logistic-regression-using-r/
3.	https://www.datacamp.com/community/tutorials/logistic-regression-R
4.	https://medium.com/greyatom/decision-trees-a-simple-way-to-visualize-a-decision-dc506a403aeb
5.	Data Mining for Business Analytics: Concepts, Techniques and Applications in R, by Galit Shmueli, Peter Bruce, Inbal Yahav, NitinPatel, and Kenneth Lichtendahl. Wiley, ISBN-10: 1118879368, ISBN-13:978-1118879368

           
                   

