# Credit-Risk-Model Project

## **Motivation** 

Ignoring credit risk was the main driver of the 2007-2008 financial crisis. In the years leading up to the crisis, banks and other lenders lent out enormous sums in the form of subprime mortgages to high-risk borrowers. As the economy slowed down between 2006 and 2007, many of these risky borrowers were unable to repay their loans, and the turmoil resulting from this systemic failure to properly account for credit risk almost destroyed the global financial system in late 2008. The big banks suffered losses because the Models they used misjudged the likelihood of mortgage defaults.

<img width="984" alt="Screenshot 2022-03-15 at 13 57 33" src="https://user-images.githubusercontent.com/94053606/158394092-ab71d404-7d99-40c3-bd71-2d0aaa6d6844.png">


Following famous rules of Warren Buffett, financial institutions should  not lend money to someone who will not pay them back.

## **Purpose**

The purpose of this project is to predict the chance of a loan being charged off, i.e. customers who are unable to pay back the loan amount. Since customers who default on a loan are a source of losses for the financial institution, it is very important to know whether or not the applicant will be able to pay back the loan amount. 

## **Problem Statement** 

'Can we build a machine learning model that can accurately predict if a borrower will pay off their loan or not?'

## **Data Source & Overview** 

https://www.lendingclub.com/info/download-data.action

Dataset used is from Lending Club, which is US peer-to peer lending company and the world’s largest p2p lending platform.  Loans issued by lendingclub are from 2007-2011 with performance data. Dataset contains 42,538 rows and 115 columns.

## **Cleaning and EDA**

_Reason behind dropping columns:_
- more than half of the columns were missing 50% or more of the data;
- some of the columns had information that was redundant or had information about loans that were already funded;
- some of columns that had no effects on borrower’s ability to repay the loan.

_Defining Dependent Variable and cleaning of Independent Variables:_
- detecting and treating  Outliers using IQR;
- dealing with missing values by replacing them with class  mean;
- dummifying categorical values;
- further removing columns which required too much feature engineering.

### Loan Status column is the target 

<img width="1004" alt="Screenshot 2022-03-15 at 12 57 06" src="https://user-images.githubusercontent.com/94053606/158382591-60d0a09b-009b-4b79-956a-0763038036b0.png"> 

Where:

#### 0 - Fully Paid
with value counts = 33586

#### 1 - Charged Off
with value counts = 5653

_**Some interesting facts found, when performing EDA**:_

### Verification Status column
Verification status indicates if income was verified by LC, not verified or if the income source was verified by an outside agency.  In this case we can see that over 14  000 loans were funded without verification.

<img width="1002" alt="Screenshot 2022-03-15 at 13 14 00" src="https://user-images.githubusercontent.com/94053606/158385584-e7d6519b-3b08-4104-8e8f-eda032ee7355.png">

### Employment Length column
Here we notice, that the highest group of customers who are looking for a loan is a group with employment length of 10 + years (approved loans -8034). Interestingly, in second place is the group with less than one year of employment history  with 4367 approved loans.

<img width="968" alt="Screenshot 2022-03-15 at 13 21 18" src="https://user-images.githubusercontent.com/94053606/158386808-d8dfa8bf-f257-4119-8b4e-605eeeefbec2.png">

### Term column
This is a number of payments on the loan. It can be either  over 36 or 60 months . As we can see, loans for 36 months constitute a much larger group. However, default loans occur over twice more frequently over 60 months term period (24%) then on 36 (11%).

<img width="962" alt="Screenshot 2022-03-15 at 13 22 52" src="https://user-images.githubusercontent.com/94053606/158392946-fdff66c6-0e44-4219-912e-93af0f2164c4.png">

## **Results**

### Baseline = 0.8555

Models used:
- KNeighbors Classifier,
- LogisticRegression,
- DecisionTreeClassifier,
- RandomForestClassifier.

After using cross validatione, the scores are as follow:

<img width="899" alt="Screenshot 2022-03-15 at 13 31 47" src="https://user-images.githubusercontent.com/94053606/158388832-8aa17570-330e-40a7-826d-67cf23a258ac.png">

The best performers are Logistic Regression and Random Forest. The scores are only marginally better than the base line.

## **Limitations**
- Very limited choice in credit risk datasets. Lending Club Loan Dataset being the largest one available. 
- Size of my dataset, much larger dataset would predict more reliable scores.
- Time and not enough knowledge  and experience. 

## **Recommendations**
- Obtaining much larger dataset.
- Considering more features and test out different parameters for different models.

## **Conclusions**

My aim was to predict as accurately as possible customers whose loan was charged off, i.e. they were not able to fully repay their loan. I may be able to predict instances where a client will default on a loan, but this will also result in instances where the model predicts that the customer will default on a loan but will actually do so. Thus, the company will lose potential customers. If I had to recommend I would choose Random Forest Classifier after oversampling the data, as it has the best results.


