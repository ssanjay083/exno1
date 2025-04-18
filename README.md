# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
          import pandas as pd
          df=pd.read_csv("SAMPLEIDS (1).csv")
          df
![image](https://github.com/user-attachments/assets/8c84c30c-4bf4-407a-80d0-dbc4895420f0)

          df.isnull()
![image](https://github.com/user-attachments/assets/c186bf67-404e-4970-b676-34e189bcdcc6)

          df.info()
![image](https://github.com/user-attachments/assets/953ad028-917f-4e6e-9fcc-c02c4085b638)

          df.notnull()
![image](https://github.com/user-attachments/assets/9ff27e8b-43e0-4ff9-a5a2-984ac07ce787)

          df.dropna(axis=0)
![image](https://github.com/user-attachments/assets/7803481e-001c-4bf9-8274-0cc6349fc32b)

          df.dropna(axis=1)
![image](https://github.com/user-attachments/assets/58bfe1ee-e505-47b9-ad30-f73dbfaa91ec)

          dfs=df[df['TOTAL']>270]
          dfs

![image](https://github.com/user-attachments/assets/6776e58a-5373-4d31-b40e-ffd86bc665dc)

          df.iloc[:4]
![image](https://github.com/user-attachments/assets/4716395d-1c9d-46a9-9515-3bffbff6118a)

          df.iloc[0:4 , 1:4]
![image](https://github.com/user-attachments/assets/e86a8188-42f0-4abe-9b33-3874712402a2)

          df.iloc[[1,3,5],[1,3]]
![image](https://github.com/user-attachments/assets/6a9291c1-3dce-411b-af43-c162dc72bdc2)

          dfs=df[df['NAME'].str.startswith(('A','C'))&(df['TOTAL']>250)]
          dfs
![image](https://github.com/user-attachments/assets/e66be4b6-c6e1-4289-a09e-40699a801036)

          dff=df.fillna(0)
          dff
![image](https://github.com/user-attachments/assets/1a71ce54-c5b4-40c6-8928-d3bd06160d51)

          df.fillna(method="ffill")
![image](https://github.com/user-attachments/assets/4276abc4-7576-45b0-8794-29c2c7e409fe)

          df.fillna(method="ffill")
![image](https://github.com/user-attachments/assets/44126407-54ab-4f32-9cce-2e238cefbfd7)

          df['TOTAL'].fillna(value=df['TOTAL'].mean())
![image](https://github.com/user-attachments/assets/3651dde1-8e51-4067-8ce6-d6e653bae2fb)

          df.isnull().sum()
![image](https://github.com/user-attachments/assets/f07e39da-1343-448f-9b67-6fc5d0164faa)

          df.dropna(how='any')
![image](https://github.com/user-attachments/assets/5a539fbf-91b0-4b7b-92c6-797caaf5ccd7)

          df.dropna(how='all')
![image](https://github.com/user-attachments/assets/10fb1644-d1a5-40e3-b605-a00d3a496402)

          mn=df.TOTAL.mean()
          print(mn)
![image](https://github.com/user-attachments/assets/9536270a-3f64-4681-87a1-b1228a16205d)

          df.fillna(mn,inplace=True)
          df
![image](https://github.com/user-attachments/assets/744930c5-399f-4c76-b09c-c8ac40db5096)

          df.isna().sum()
![image](https://github.com/user-attachments/assets/79828241-cb62-4955-b6a6-c790e0e16cbf)

          import seaborn as sns
          sns.heatmap(df.isnull(),yticklabels=False,annot=True)
![image](https://github.com/user-attachments/assets/06938a5e-0de0-4c8b-b51a-a5e1410c1ed2)

          df.dropna(inplace = True)
          sns.heatmap(df.isnull(),yticklabels=False,annot=True)
![image](https://github.com/user-attachments/assets/2cde5b0f-bada-4730-a251-4400742cc384)

          OUTLIER DETECTION
          import pandas as pd
          import seaborn as sns
          import numpy as np
          age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
          af = pd.DataFrame(age)
          af
![image](https://github.com/user-attachments/assets/485a55e8-50e0-432a-a1d6-adff760a0613)

          sns.boxplot(data=af)
![image](https://github.com/user-attachments/assets/63a4304d-051a-4228-a2f4-a78f8b1dc137)

          sns.scatterplot(data=af)
![image](https://github.com/user-attachments/assets/4c7b4d02-6da1-45ea-85ce-e2394ed886b5)


          q1 = af.quantile(0.25)
          q2 = af.quantile(0.50)
          q3 = af.quantile(0.75)
          iqr = q3 - q1
          q1, q2, q3, iqr
![image](https://github.com/user-attachments/assets/90ac9679-a682-464d-a332-09f1e0b42b57)

          Q1 = np.percentile(af, 25)
          Q3 = np.percentile(af, 75)
          IQR = Q3 - Q1
          Q1, Q3, IQR
![image](https://github.com/user-attachments/assets/0ba5bbe2-f92c-4cd3-8157-e614f1d9584f)

          lower_bound = Q1 - 1.5 * IQR
          upper_bound = Q3 + 1.5 * IQR
          lower_bound
![image](https://github.com/user-attachments/assets/c7a091d7-a843-429f-baa9-0942278a6bb5)

          upper_bound
![image](https://github.com/user-attachments/assets/aa56a91f-ff5a-4af2-83bf-519066909b03)

          af = af[(af >= lower_bound) & (af <= upper_bound)]
          af
![image](https://github.com/user-attachments/assets/e1128d99-3ca2-47c9-af32-c5be1a246b77)

          sns.boxplot(data=af)
![image](https://github.com/user-attachments/assets/110e49b6-649a-4c7e-a01f-98310398a016)

          sns.scatterplot(data=af)
![image](https://github.com/user-attachments/assets/7f6dc137-4393-492e-98e5-962a600ed000)

Z SCORE METHOD
          
          data=[1,2,2,3,1,1,15,2,2,2,3,1,1,2]
          mean = np.mean(data)
          std = np.std(data)
          print('mean of the dataset is',mean)
          print('std. deviation is',std)

![image](https://github.com/user-attachments/assets/867cb443-8a4c-4fca-a523-37ae3eb9925c)

          threshold = 3
          outlier = []
          for i in data:
              z=(i-mean)/std
              if z > threshold:
                  outlier.append(i)
          print('outlier in dataset is',outlier)
![image](https://github.com/user-attachments/assets/710673a7-56ef-4ebd-b17e-cd52e329325e)

          import numpy as np
          import seaborn as sns
          import pandas as pd
          from scipy import stats

           data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
          df=pd.DataFrame(data)
          df
![image](https://github.com/user-attachments/assets/bbfece97-5773-47b0-8979-3b2f3230c449)

          z = np.abs(stats.zscore(df))
          print(df[z['weight'] > 3])
![image](https://github.com/user-attachments/assets/13984e38-8da6-4808-8722-5d1965792b64)

          val = [12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]
          out = []
          def d_o(val):
              ts = 3
              m = np.mean(val)
              sd = np.std(val)
              for i in val:
                  z = (i - m) / sd
                  if np.abs(z) > ts:
                      out.append(i)
              return out

          op = d_o(val)
          op
![image](https://github.com/user-attachments/assets/add4d603-3dd5-4183-93fc-d13a52359e9f)
          
# Result
          Thus, we have carried out data cleansing and removed the outliers by detection using IQR and Z-Score methods. The cleaned data has been successfully prepared for further analysis.
