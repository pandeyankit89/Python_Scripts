#### Day-3
---
#### Pandas:
- `Pandas` full form is : `Pa`nel `Da`ta `S`ystem.
- Open-source, BSD-licensed
- It is a `Data Exploration tool/library`.
- It is used for `Data Analytics`.
    - `Data-Analytics` : Collection + Explore + Clean +Visualization of data
        - Answer questions like `what is noraml or what is abnormal ?` or `to spot some trends`.
        - helps to make `strategies`.

- Two types of Statistics : 
    - (1) `Descriptive Stats` - Summarize metrics
        - (a) `Univarient` : like mean,median, min, max, std
        - (b) `Multi-varaient`: correaltion
    - (2) `Inferential Stats` - Making inference out of analysis. Test changes (e.g did a new firewall rule reduced threats)
- `Probability` - Quantify risks (e.g. likelihood of DDos attack)
- `Practical for IT` - Monitor uptime, validate config, assess risks

#### Use-cases for Network/Infrastructure/AD/Security Enggineers:
- `Analytics/Stats` : Analyzinf traffic (netflow, SNMP), detect bottlenecks with varience, Tracking login patterns, failed attempts
, SIEM data anaylis, threat hunting
- `Pandas` filter high latency events, correlate with time-of-day, monitor CPU/Memory, forecast storage, VM logs,Parse AD log, analyze group policy compliance, filter firewall logs
-`ML\Deep Learning` : Two types :
    - (1) `Supervised ML`: Data-driven decision making.
    - (2) `Un-supervised ML` : Grouping data based on simillarities
    - Use case : sentiment analysis, Predicting failure, optimize traffic, anomaly detection, predictive and solving DDoS attac,Predicting Hardware failure, Detecting insider threat
-`Real-World` - Cisco DNAC Center uses ML for `intent-based networking`. AWS Predictive Scaling optimize cost, `Microsoft Defender` for Identity uses ML for AD security, `Sitecore Cortex`
---
#### Pandas Data-Structures:
- Pandas offers 2 `Ordered` Data-Structures :
    - (1)`Series` : 1-dimentional or `1-column (not row)` + it has `index-number`
    - (2) `Dataframes` : collection of rows and columns or more than one Series 

- Import pandas library as 
```python
import pandas as pd
```

#### Series :
- 1-dimentional but as  `a column (not row)` 
- `Ordered` as having index number
```python
s =pd.Series([120,150,90,200,110])

#0    120
#1    150
#2     90
#3    200
#4    110
#dtype: int64
```
- `s.index`: gives number of items `RangeIndex(start=0, stop=5, step=1)`
- `dt = pd.date_range(start='20250901', periods=5)` : is used to add `date-range` as an index by assiging `s.index = dt`
    - use `freq='1D'` or `freq='3M'` to set Daterange as Daily or Quaterly
---
```python
#pip install pandas
import pandas as pd
s =pd.Series([120,150,90,200,110])
print(s) # All Series
print(s[0]) # First index items
print(s[:2]) # All itesm till (n-1) index, total n items
print(s.index)
```
```python
#Step 1 : Create a DateTimeIndex in count same as number of items in Series/Data-Frame
dt = pd.date_range(start='20250901', periods=5)
#DatetimeIndex(['2025-09-01', '2025-09-02', '2025-09-3', '2025-09-4','2025-09-5'],dtype='datetime64[ns]')

#Step 2: Make this DateTimeIndex as Series Index
s.index = dt

# Stpe 3: Insread of number [0-4] as index, now date-time will be show as index
print(s) # Index number will be changed to date like 'yyyy-mm-dd' 
print("----------")
print(s['2025-09-04']) #  Gives value for this index only.
print("----------")
print(s[:'2025-09-03']) #  Gives data till 03rd-Sep
print("----------")
print(s[2]) #But still works
```
```python
s.index=['Server1','Server2','Server3','Serevr4','Server5']
print(s) # index will chnaged as Server-names
print("----------")
print(s[:'Serevr4']) # Provide data from start till it finds Server4.
```
#### Functions with Series :
- `s.mean()`
- `s.std()`
- `s.max()`
- `s.min()`
- `dir(s)` : to check all the functions
---
#### Dataframe :
- colletion of rows and columns
- more than 1 sereies
-`pd.DataFrame(...)` : to create a DataFrame
```python
pd.DataFrame(np.random.randn(2,4)) 
#use of NumPy randn to create and array i.e. rows and columns then converting this into DataFrame
#	   0	         1	        2	        3
#0	-1.689495	1.395712	0.561087	1.023173
#1	2.210736	-0.193013	-0.096457	-0.725069
```
- It is similar to Numpy array, but it will have `Labels` like `column-name` and `row-names`
```python
pd.DataFrame(data=[[10,11,12],[13,14,15]],columns=['A','B','C'],index=['Mon','Tue']) #Note : Data is in [[]]
#   	A	B	C
#Mon	10	11	12
#Tue	13	14	15
```
```python
import numpy as np
pd.DataFrame(np.random.randn(2,4))

#		0			1			2			3
#0	0.219965	0.221734	-1.052361	-1.700102
#1	0.686175	0.222253	0.320160	1.672341
```
```python
pd.DataFrame(data=[[10,11,12],[13,14,15]],columns=['A','B','C'],index=['Mon','Tue']) #Note : Data is in [[]]

#		A	B	C
#Mon	10	11	12
#Tue	13	14	15
```
- Easiest way to create a DataFrame is to by using `dictionary`
```python
df = pd.DataFrame({'Server':['Web1','Web2','DB1','DB2','App1'],
                    'CPU_Usage':[75,60,85,45,70],
                    'Uptime_Hours' : [720,600,800,500,650]})
df
```
```python
df = pd.DataFrame({'Server':['Web1','Web2','DB1','DB2','App1'],
                    'CPU_Usage':[75,60,85,45,70],
                    'Memory_Usage':[50,60,70,80,60],
                    'Uptime_Hours' : [720,600,800,500,650]})
df

#   Server	CPU_Usage	Memory_Usage	Uptime_Hours
#0	Web1	75	            50	            720
#1	Web2	60	            60	            600
#2	DB1	    85	            70	            800
#3	DB2	    45	            80	            500
#4	App1	70	            60	            650
```
#### Accessing data of DataFrame and use of Slicing -
- `df` = show all dataframe
- `df[:4]` = show first 4 rows
- `df[3:4]` = print only 4th row
- `df['<column-name>']` like `df['Server']` will show Server column
- `df[['<column-name1>','<column-name2>']]` like `df[[]'Server','CPU_Usage']]` will show Server and CPU_Usage columns. *_Note_*: use `[[]]`
-`df[['<column-name1>','<column-name2>']][:n]` = `df[:n][['<column-name1>','<column-name2>']]` => gives first 3 rows
- `df.index = ['A','B','C','D','E']` => add index name.*_Note_*: count of items should be same as number of rows.
- `df.reset_index()` for Temporary or `df.reset_index(inplace=True)` for permanent operation =>  to make index lable as one column and create a new index with numbers 0..n 
```text
                index	Server	CPU_Usage	Memory_Usage
        0	flask	Web1	75			50
        1	Django	Web2	60			60
        2	mysql	DB1	85			70
        3	oracle	DB2	45			80
```
- `df.rename(columns={"index":"softwares"})` : To rename the new-index column as "software"
```text
            softwares	Server	CPU_Usage	Memory_Usage
        0	flask	Web1	75	        50
        1	Django	Web2	60	        60
        2	mysql	DB1	85	        70
        3	oracle	DB2	45	        80
```
- `df.reindex(<new-index-name which should a list of exact length>)` : only new entries will be applicable. matching ones will be untouched.
- *_None_* : Blank values will be shown as `NaN`.

- Accessing DataFrame's data by using -
    - `Indexing` --> grabiing data like `df[3:4]`
    - `[]` --> Access `single-column` by label names like `df['<column-name1>']`
    - `[[]]` --> Access `multiple-columns` by label names like `df[['<column-name1>','<column-name2>']]`
    - `loc` --> Access both rows & columns `by label`, like :
        - `df.loc[['<index-name1>','index-name2']][['<column-name1>','<column-name2>']]`
    - `iloc` --> Access data based on `integer based indexing`, like :
        - `df.iloc[row_index_numbers_in_list,column_index_numbers_in_list]` for mentioned row-index and col-index
        - `df.iloc[row_index_numbers_in_list,:]` for mentioned row-index and all columns
        - `df.iloc[:,column_index_numbers_in_list]`  for all rows and mentioned column-index
        - `df.iloc[:,:]`  for all rows and all columns
        - `df.iloc[:,column_slicing_as start:stop:step]`  for all rows and mentioned column-indexes as `start:stop:step`
         - `df.iloc[row_slicing_as start:stop:step, :]`  for row-indexes as `start:stop:step` and all columns
```python
df.index = ['flask','Django','mysql','oracle','ecom']
df[['Server','CPU_Usage']]
#		Server	CPU_Usage
#flask	Web1	75
#Django	Web2	60
#mysql	DB1	    85
#oracle	DB2	    45
#ecom	App1	70
```
```python
df.loc[['flask','oracle']][['Server','CPU_Usage']]

#	    Server	CPU_Usage
#flask	Web1	75
#oracle	DB2	    45
```
```python
df.iloc[[0,1,4],[0,2,3]]
#	        Server	Memory_Usage	Uptime_Hours
#flask	    Web1	  50	        720
#Django	    Web2	  60	        600
#ecom	    App1	  60	        650
```
#### Data-Manipulation in DataFrame :
- *Adding a New Column* : 
    - _As a Last column_ => `df['<new-column-name>'] = ['A',"B'...till number of exact items]`. Example -
        - `df['Grade'] = ['A','B','C','D','E']`
    - _At a Specific Numner_ => `df.insert(<column-index-number_where_to-insert-new-column>,'<new-column-name-inside-quotes',[values inside list])`. Example -
        - `df.insert(2,'Grades',[100,20,'A','A++',5])`
        - _Note_: `allow_duplicates` default is `False`. needs to enable for duplicate columns
            - `df.insert(2,'Grades',[100,20,'A','A++',5],allow_duplicates=True )`
- *Adding a New Row* :
    - *_using iloc()_*: `df.iloc['<row-name>']=[col1-value,col2-value,....colN-value]`
- *Drop a Row/Column*:
    - `df.drop('<row-index-name>')` as `default axis is 0 means row`
    - `df.drop('<column-name>', axis=1)` as *set axis to 1 means column*

    - *Note* : `df.insert()` is `permanent` while `df.drop() is temporary` 
    - *_Note_*: To make the change permanent instead of temporary, use either :
        - `df = df.drop(...)`  or
        - `df.drop(..., inplace=True)`  : by using `inplace=True`

```python
df['Grades'] = ['A','B','C','D','E'] #This will add a column 'Grades' in last
df

#        Server	CPU_Usage	Memory_Usage	Uptime_Hours	Grades
#flask	Web1	75	        50	            720	            A
#Django	Web2	60	        60	            600	            B
#mysql	DB1	    85	        70	            800	            C
#oracle	DB2	    45	        80	            500	            D
#ecom	App1	70	        60	            650	            E
```
```python
#help(df.insert)
df.insert(2,'Grades',[100,20,'A','A++',5],allow_duplicates=True) #This will add a duplicate column 'Grades' at 2nd column
df

#	    Server	CPU_Usage	Grades	Memory_Usage	Uptime_Hours	Grades
#flask	Web1	75			100			50				720				A
#Django	Web2	60			20			60				600				B
#mysql	DB1	    85			A			70				800				C
#oracle	DB2	    45			A++			80				500				D
#ecom	App1	70			5			60				650				E
```
```python
df = df.drop('ecom') # Drop a Row by label-name
df = df.drop('Grades',axis=1) #Drop a Column by label-name with property axis=1, making drop operation permanent by df = df.drop(...) 
df

#		Server	CPU_Usage	Memory_Usage	Uptime_Hours
#flask	Web1	75				50				720
#Django	Web2	60				60				600
#mysql	DB1		85				70				800
#oracle	DB2		45				80				500
```
```python
df.drop('Uptime_Hours',axis=1,inplace=True)  #making drop operation permanent by df = df.drop(..., inplace=True) 
df

#	Server	CPU_Usage	Memory_Usage
#flask	Web1	75			50
#Django	Web2	60			60
#mysql	DB1		85			70
#oracle	DB2		45			80
```
#### Conditional Sub-Setting : Accessing Dataframe based on Condition:
- `df[df['<col-name>'] operator(==,>,>) value]`. Example -
```python
    df[df['CPU_Usage']>45]
```
- `df[(df['<col-name>'] operator(==,>,>) value) & or | (df['<col-name>'] operator(==,>,>) value)]`. Example -
    ```python
    df[(df['CPU_Usage']==45) | (df['CPU_Usage']==75)]
    ```
- *_Note_* : to print in proper way we have to use df inside df
```python
df[df['CPU_Usage']>45]

#		Server	CPU_Usage	Memory_Usage
#flask	Web1	75				50
#Django	Web2	60				60
#mysql	DB1		85				70
```
```python
df[(df['CPU_Usage']==45) | (df['CPU_Usage']==75)]

#		Server	CPU_Usage	Memory_Usage
#flask	Web1	75			50
#oracle	DB2		45			80
```
---
#### Accessing using String functions -
```python
df[df['Server'] == "db2".upper()] 

#or

df[df['Server'].str.lower() == "db2"] 

#		Server	CPU_Usage	Memory_Usage
#oracle	DB2		45				80
```
```python
df
#		Server	CPU_Usage	Memory_Usage
#flask	Web1	75			50
#Django	Web2	60			60
#mysql	DB1		85			70
#oracle	DB2		45			80


df.reset_index(inplace=True)

df.rename(columns={"index":"softwares"})

#	softwares	Server	CPU_Usage	Memory_Usage
#0	flask		Web1	75				50
#1	Django		Web2	60				60
#2	mysql		DB1		85				70
#3	oracle		DB2		45				80

df.reset_index(drop=True, inplace=True)
```
#### sorting functions :
- `df.sort_index(ascending=False)` : sorting data based on indexing
- `df.columns` : list the column-names
- `df.sort_values(by='<column-name>')` : sorting data based on column value
---
#### Data-Science Lifecycle:

- *Step 1* is *_Data Engineering_* : Collect, store, process & manage 
    - Poluar Tools are - RDBMS, DWH, Hadoop/spark, cloud
- *Step 2* is *_Data Analytics_* : Analysis, maths, stats 
    - Popular Tools are R, Pandas, SQL
- *Step 3* is *_Business Intelligence_* : Dashboard
    - Popular Tools are Power-BI, Tablue, Qlickview
- *Step 4* is *_Advanced Analytics_* : creating ML models, Deep-Learning, AI
- *Step 5* is *_Solution Development_* : Provide solution

---
### Exploratory Data Analysis (EDA)

- We analyze in 2 ways :
    - (1) `Uni-variate` : analyzing one column at a time
    - (2) `Multi-variate` : analyzing two or more columns at a time

- *_Descriptive Statistics_*: Look as data as it is. Summarize the data without any assumption. It has 3 measures:

    - *(1) Measure of Central Tendency of Data* : mean, median, mode
        - `df['<col-name>'].mean()`
        - `df['<col-name>'].median()`
        - _Note_: if huge difference in `mean` and `median` then *data distribution is not normal*.
        - If data is normaly dostributed then :
            - ~68% area → Data lies within **±1 standard deviation (σ)** of the mean (most values close to mean).  
            - ~95% area → Data lies within **±2σ** of the mean (almost all typical values).  
            - ~99.7% area → Data lies within **±3σ** of the mean (extreme but still normal values).  
            - This is called the *_Empirical Rule (68–95–99.7 Rule)_*.
            <div align="center"><img src="/img/emperical_rule.png" alt="Empirical Rule" style="width:30%; height:30%;" /></div>
        - `df['<col-name>'].mode()` : mostly used for characher data
        
    - *(2) Measure of Dispersion* : range as min and max, variance (how far away each item from mean, but we take square to avoid negative value), std dev (square-root of varaince), quartiles
        - `df['<col-name>'].min()`
        - `df['<col-name>'].max()`
        - `df['<col-name>'].var()` : sqaured difference from mean
        - `df['<col-name>'].std()` : square-root of variance. For normally dostributed data, it should be minimum.

        - `sns.boxplot(df['<col-name>'])` : box-plot  to understand quartile
        - `sns.boxplot(x= df['<col-name>'])` : <u><b>Horizontal</b></u> box-plot  to understand quartile
            - _Box-Plot_ shows info from top to bottom as `Max -> 75% -> Median -> 25% -> Min`. It will also show `outliers` 
        - *_Note_* : std-dev by formula and std-dev in Excel is different as Excel usage <> method to calculate.
        - _Important Formulas related to boxplot_:
            - `IQR = Q3 -Q1`
            - `Upper whisker = Q3 + 1.5(IQR)`
            - `Lower whicker = Q1 - 1.5(IQR)`
            - `Outlier` = `anything greater than Upper whisker` or `anything lower than Lower whicker`
        - `df['<col-name>'].quartile(0.25)` : First Quartile value
        - `df['<col-name>'].quartile(0.75)` : Third Quartile value
        <div align="center"><img src="/img/boxplot.png" alt="Boxplot" style="width:30%; height:30%;"/></div>

    - *(3) Measure of Shape* : skewness, kurtosis
        - `(1) Degree of Skewness` : means which side data is more alligned like lef-skiwed or right-skewed 
            - `df['<col-name>'].skew()`
            - Note : 
                - *Symmetric (Skewness = 0)* → Data evenly spread, mean ≈ median ≈ mode.  
                - *Positively Skewed (Right-Skewed)* → Long tail on right, mean > median > mode.  
                - *Negatively Skewed (Left-Skewed)* → Long tail on left, mean < median < mode.  
                - *Highly Skewed* → Extreme long tail, data concentrated heavily on one side.  
                - *Moderately Skewed* → Noticeable tail but not extreme.  
                - *Approximately Symmetric* → Slight skew but close to normal distribution.  

       - `(2) kurtosis` : is an indication to show how skewed your data is. `sharpness of the peak in frequency-distribution`.
            - `df['<col-name>'].kurt()`
            - 3 type of Kutosis :
                - *Mesokurtic* : Normal distribution with medium peak and tails (reference kurtosis = 3).  
                - *Leptokurtic* : Distribution with a sharp peak and heavy tails (kurtosis > 3).  
                - *Platykurtic* : Distribution with a flat peak and light tails (kurtosis < 3).  
    

    - *_Some more functions realted to dataframes_* :
        - `df.describe()` : to show all descriptive data `for numerical columns`.
        - `df['<col-name>'].describe()` : to show all descriptive data `for a specific numerical column`.
        - `df.T` : to transpose the data
        - `df['<col-name>'].unique()` → Returns all the **unique values** in the column as an array.  
        - `df['<col-name>'].nunique()` → Returns the **count of unique values** in the column.  
        - `df['<col-name>'].value_counts()` → Returns a **count of each unique value** in the column (frequency table).  

---
- To read a CSV or JSON file use :
    - `pd.read_csv("<Filename wiht Path with />")` don't use \ as it a escape sequence in python or 
        - `pd.read_csv("<Filename>", sep='\t')` : if file is tab seperated. Default seperator is comma.
        - `pd.read_csv("<Filename>", skiprows=n)` : to skip n-line from top.
    - `pd.read_json()`

- Basic Questions :
    - How much data /size of data ? : `df.shape` #(10000, 10)
    - Columns Name ? : `df.columns` #Index(['start_time', 'end_time', 'duration_sec', 'src_ip', 'dst_ip','protocol', 'src_port', 'dst_port', 'bytes', 'packets'],dtype='object')
    - Datatype of each columns ? :`df.info()`
        - _Note_: `object` Dtype = `string` 
    ```text
                RangeIndex: 10000 entries, 0 to 9999
                Data columns (total 10 columns):
                #   Column        Non-Null Count  Dtype 
                ---  ------        --------------  ----- 
                0   start_time    10000 non-null  object
                1   end_time      10000 non-null  object
                2   duration_sec  10000 non-null  int64 
                3   src_ip        10000 non-null  object
                4   dst_ip        10000 non-null  object
                5   protocol      10000 non-null  object
                6   src_port      10000 non-null  int64 
                7   dst_port      10000 non-null  int64 
                8   bytes         10000 non-null  int64 
                9   packets       10000 non-null  int64 
                dtypes: int64(5), object(5)
                memory usage: 781.4+ KB
    ```
```python
df = pd.read_csv("netflow_dataset.csv") #Not need to put path as file in same directory.
df[:2] # to check first 2 values, or
df.head(2) # to check first 2 values

#	start_time	end_time	duration_sec	src_ip	dst_ip	protocol	src_port	dst_port	bytes	packets
#0	2025-09-08 09:37:41.532032	2025-09-08 09:40:31.532032	170	10.0.2.169	172.16.8.40	TCP	80	80	269145	307
#1	2025-09-08 08:53:30.532032	2025-09-08 08:53:46.532032	16	10.0.3.173	172.16.7.117	TCP	22	110	162780	137
```
```python
df.tail(2) # to check last 2 values

#	start_time	end_time	duration_sec	src_ip	dst_ip	protocol	src_port	dst_port	bytes	packets
#9998	2025-09-09 05:36:06.532032	2025-09-09 05:37:44.532032	98	10.0.9.99	172.16.0.76	TCP	3389	25	157539	168
#9999	2025-09-08 17:22:46.532032	2025-09-08 17:23:17.532032	31	10.0.9.200	172.16.8.125	TCP	110	25	465476	1285
```
```python
df.shape #(10000, 10)
```
```python
df.columns 
#Index(['start_time', 'end_time', 'duration_sec', 'src_ip', 'dst_ip','protocol', 'src_port', 'dst_port', 'bytes', 'packets'],dtype='object')
```
```python
df.info()

#RangeIndex: 10000 entries, 0 to 9999
#Data columns (total 10 columns):
# #   Column        Non-Null Count  Dtype 
#---  ------        --------------  ----- 
# 0   start_time    10000 non-null  object
# 1   end_time      10000 non-null  object
# 2   duration_sec  10000 non-null  int64 
# 3   src_ip        10000 non-null  object
# 4   dst_ip        10000 non-null  object
# 5   protocol      10000 non-null  object
# 6   src_port      10000 non-null  int64 
# 7   dst_port      10000 non-null  int64 
# 8   bytes         10000 non-null  int64 
# 9   packets       10000 non-null  int64 
#dtypes: int64(5), object(5)
#memory usage: 781.4+ KB
```
```python
## To check central tendaency -
df['packets'].mean()   #np.float64(1166.4976)
df['packets'].median() #np.float64(637.0)
```
```python
# To ckeck Dispersion -
df['packets'].min()  #np.int64(0)
df['packets'].max()  #np.int64(17678)
df['packets'].std() #np.float64(1747.1507513002468)
```
```python
import seaborn as sns
import warnings
warnings.filterwarnings('ignore')

sns.distplot(df['packets']) #plot a graph Density vs packets
```
```python
sns.boxplot(df['packets'])    # Vertical box-plot
sns.boxplot(x=df['packets'])   # Horizontal box-plot
```
- `Uni-variate` data analysis using `matplotlib`
    - `matplotlib.pyplot` is widley used in python for visualization.
    - `plt.plot(df['<col-name>'])` : Plot as Line chart
    - `plt.hist(df['<col-name>'])` : Plot as Histogram
    - `plt.hist(df['<col-name>'], bins=n)` : Plot as Histogram with bins size as n (int)
```python
import matplotlib.pyplot as plt
plt.plot(df['packets'])

plt.hist(df['packets'], bins=25)
```
```python
df.describe()
#df['packets'].describe()

#		duration_sec	src_port		dst_port		bytes			packets
#count	10000.000000	10000.000000	10000.000000	10000.000000	10000.000000
#mean	151.478100		592.698300		588.862500		498822.549200	1166.497600
#std	86.324238		1155.363826		1152.303425		290533.221555	1747.150751
#min	1.000000		22.000000		22.000000		304.000000		0.000000
#25%	76.000000		25.000000		25.000000		243843.500000	309.000000
#50%	154.000000		80.000000		80.000000		500102.500000	637.000000
#75%	225.000000		443.000000		443.000000		750396.000000	1207.250000
#max	300.000000		3389.000000		3389.000000		999942.000000	17678.000000
```
---

