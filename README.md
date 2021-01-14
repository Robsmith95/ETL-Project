CREDIT CARD TIME!

In this ETL Project, I decided to get credit card information in which I used two CSV files. One that contains the Defaulting of Credit Card by customers named Default.csv, and I used DefaultCreditCard.ipynb, and the second one contains Charge off Rate of Credit Cards/Loans by Businesses' named Default2.csv, and I used ChargeOffRateCreditCards.ipynb/ ChargeOffRateCreditCards2008-2010.ipynb.

1. DefaultCreditCard.ipynb
This was again, customers Defaulting on their credit cards where I wanted just to view the Limit Balance, Sex, Education and Age.
Steps:
    - I first read the file Default.csv.
    - I then specified the columns that related to what I wanted to view eg.(X1 = Limit Balance)
    - Then the columns like example above were renamed {"X1" : "LIMIT_BAL", "X2" : "SEX", "X3" : "EDUCATION", "X5" : "AGE"})
    - Then with the selected and renamed columns, I connected it to a local database called CreditCardAnanlysis with the specied Columns 
    - Finally, I confirmed the data has been added by querying the balance_limit table located in PgAdmin

2. ChargeOffRateCreditCards.ipynb
For the second csv file, we are exploring the rates of Charge Off by businesses supplied by the Federal Reserve, in which we just wanted to view the date of the rate (by day) and the rate, in a similar format to what I did with DefaultCreditCards.ipynb
Steps: 
    - to begin, I renamed the file to Default2.csv and read the file. As displayed, it showed a realtime_start and realtime_end which was only showing when this csv file was updated since they are all the same dates.
    - in order to just show the date and value, I removed the header columns realtime_start and realtime_end
    - I then proceeded to rename the header columns {"date" : "Date", "value" : "Charge_off_Rate"})
    - Then with the selected and renamed columns, I connected it to a local database called CreditCardAnanlysis2 with the specied Columns 
    - Finally, I confirmed the data has been added by querying the 'fredcor' table located in PgAdmin

3. ChargeOffRateCreditCards2008-2010.ipynb
While this applies to the second csv file, I wanted to just show the Charge off Rates during the economic crash of 2008, with my goal of having 2008-2010 just showing.
 Steps:
    - While essentially the same as above, the extra step added was to loop through and specify the rows I wanted after reading just 'date' and 'Charge off Rate'
    - in order to achieve this, we are creating a Python list of boolings that have a length in between 2008-2010.
    - The booling will be true if a given row is between 2008-01-01 and 2010-12-31, otherwise false
    - I created a list of booleans under the condition 
    if length >= "2008-01-01" and length < "2010-12-31":
        booleans.append(True)
    else: 
        booleans.append(False)
    - In order to make sure it looped through all the rows, we len(booleans) in which we had a result of 298 rows being looped through
    - Once read, we found that we had the results needed. 
    - After this process, we did what was shown above, renaming the columns and then connecting it to a local database under the same name CredCardAnalysis2, and renamed the table from fredor to fredcor08_10 through Jupyter Notebook.
    - We then read the sql query where we had the same results as the ChargeOffCreditCards.ipynb but with 2008-2010 only being listed.