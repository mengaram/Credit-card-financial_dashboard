# Credit-card-financial_dashboard
power bi dashboard
project objective : To develop a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively. 
steps: 1. Prepare csv file
2. Create tables in SQL
3. import csv file into SQL
dax queries :AgeGroup = SWITCH( 
          TRUE(), 
             'public cust_detail'[customer_age] < 30, "20-30", 
             'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40“ ,
          'public cust_detail'[customer_age] >= 40 && ‘public cust_detail'[customer_age] < 50, "40-50“, 
              'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60“, 
               'public cust_detail'[customer_age] >= 60, "60+", 
              "unknown” 
            ) 

         IncomeGroup = SWITCH( 
           TRUE(), 
          'public  cust_detail'[income] < 35000, "Low",  
           'public  cust_detail'[income] >= 35000 && 'public cust_detail'[income]<70000, “med” , 
           'public  cust_detail'[income] >= 70000, "High",
          "unknown" 
dax queries :week_num2 = WEEKNUM('public cc_detail'[week_start_date])
Revenue = 'public cc_detail'[annual _ fees] + 'public cc_detail'[total_trans_amt ]  + 'public cc _detail’ [interest _ earned] 

Current _week_ Reveneue = CALCULATE(
           SUM('public cc _detail’ [Revenue]),
           FILTER(  
                  ALL('public cc _detail ’),
                 'public cc _detail’ [week_num2] = MAX('public cc _detail’ [week_num2])))                                                 
Previous _week _Reveneue= CALCULATE(
     SUM('public cc_detail Revenue]),
     FILTER(
            ALL('public cc-detail’), 
            public cc _ detail'[week_num2] = MAX('public cc _detail” [week_num2])-1))

insights:WoW change: 
• Revenue increased by 28.8%,
• Total Transaction Amt & Count increased by xx% & xx%
• Customer count increased by xx% 
Overview YTD:
• Overall revenue is 57M 
• Total interest is 8M
• Total transaction amount is 46M
• Male customers are contributing more in revenue 31M, female 26M 
• Blue & Silver credit card are contributing to 93% of overall transactions         
• TX, NY & CA is contributing to 68%                                                                  
• Overall Activation rate is 57.5%                                                                       
• Overall Delinquent rate is 6.06%



