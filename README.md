# IBM-Employee-Attrition

Attrition, in Human Resource terminology, refers to the phenomenon of the employees leaving the company. Attrition in a company is usually measured with a metric called attrition rate, which simply measures the no of employees moving out of the company (voluntary resigning or laid off by the company). Attrition Rate is also referred as churn rate or turnover. An organization is only as good as its best employees. In an ever-changing economy, it is getting harder and harder to retain best employees. You might be able to offer respectable wages, perks and a great working environment but there will be several other factors that come into play.
Data Description:
The dataset has 35 columns and 1470 entries. The dataset includes both nominal and interval data. Attrition is the label in our dataset and would like to find out why employees are leaving the organization. 1237 (84% of cases) employees did not leave the organization while 237 (16% of cases) did leave the IBM organization making our dataset to be considered imbalanced since more people stay in the organization than they actually leave.
 
Data Cleaning & Preparation:
In the real world however, most of the time, Data will be presented in all sorts of forms and conditions. Being able to effectively clean, combine and prepare data will set up for success whenever striving to build a model. As this dataset is from Kaggle, dataset is relatively clean, any cleaning done is mainly to improve quality of life for coding. Columns such as education that are numerical that actually represent categorical variables may need further investigation. EmployeeCount is a constant column with all values being 1. Performance rating whilst being on a scale of 1-4, only has 3s and 4s. Standard Hours is a constant column with all values being 80 hours. I have dropped the two constant columns such as 'EmployeeCount','EmployeeNumber'. I have also ordered the values of education by ranking below_college as 1 and till  Doctor as 5.


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

           
                   

