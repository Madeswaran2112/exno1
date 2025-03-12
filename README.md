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
```
import pandas as pd
```
```
df=pd.read_csv("Data_set.csv")
df
```
![421780670-696b420c-a977-46af-87b8-d4a7cb12b901](https://github.com/user-attachments/assets/47b51c05-acd5-48a3-8c27-1c6a9bfbdfab)
```
df.head()
```
![421780753-b6c551df-b164-4c30-abd5-661639cf6d5b](https://github.com/user-attachments/assets/507e9a6d-4f9e-494f-971e-c1fbb281dc12)
```
df.tail()
```
![421780887-bba033f0-abbb-4b46-a216-38c7688da822](https://github.com/user-attachments/assets/9c62a015-e1b1-4de2-a226-7adff20160f7)
```
df.info()
```
![421781232-b7324a18-ac58-4067-8766-65059ab42fad](https://github.com/user-attachments/assets/42a44928-2157-4681-86c2-0c2d7c558a71)
```
df.describe()
```
![421781347-07ad29c0-f41b-4249-b055-faf60352c4fe](https://github.com/user-attachments/assets/5908a553-6c5b-47d6-b920-1c48dad1fe5a)

```
df.isnull()
```
![421782254-41dfbf9a-050b-4dd0-99b1-c1c5971ea20a](https://github.com/user-attachments/assets/2cf9289d-2265-423d-adf6-f2379dcbddae)
```
df.notnull()
```
![421782340-c4294214-05cf-4822-b544-8e1c3a67ec14](https://github.com/user-attachments/assets/09c70bf4-4554-4edf-985a-08410bd09479)
```
sum_of_df=df.isnull().sum(axis=1)
sum_of_df
```
![421782437-509a5352-a9ab-4e2d-b6b9-3bd97a27f4d2](https://github.com/user-attachments/assets/24302068-a103-45d7-8d64-6d0eb5eb1f45)

```
drop_null=df.dropna()
drop_null
```
![421782573-c3b1f9ff-3045-42aa-9df2-87189169c59a](https://github.com/user-attachments/assets/a8d0149e-157f-4806-b805-7a07ddd8af17)

```
fill_null_value=df.fillna(0)
fill_null_value
```
![421782702-2b0fa1f2-0a86-44e2-bd2e-747dfd44dccd](https://github.com/user-attachments/assets/1cb61830-c708-4695-86e2-74496d79ad96)

```
null_with_ffill=df.fillna(method='ffill')
null_with_ffill
```
![421782839-959e83aa-e594-443f-9c56-cfee491efabf](https://github.com/user-attachments/assets/7f503873-c51b-4c87-a94a-4c3de2796fb1)

```
null_with_bfill=df.fillna(method='bfill')
null_with_bfill
```
![421783046-c9d9891b-4c36-4ccb-86a1-15381d1ff418](https://github.com/user-attachments/assets/a948d8aa-d2c9-481e-b3f0-114d9e6d7309)

```
mean_value = df['num_episodes'].mean()
mean_value
df['num_episodes'] = df['num_episodes'].fillna(mean_value)
df.head()
```
![421783215-03b82c1e-081c-4086-be5f-66c803120f4f](https://github.com/user-attachments/assets/88d603c2-1da2-4141-8fab-58413a29c50a)

```
import pandas as pd
import numpy as np
import seaborn as sns
```
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![421784059-b6606ae2-4d22-44bf-9c00-8b5a5c226114](https://github.com/user-attachments/assets/038b179c-a582-403e-a709-50da30e95f1d)

```
sns.boxplot(data=af)
```
![421784203-59b66dc6-d5a9-4fdc-8ce8-14fbb700c0f5](https://github.com/user-attachments/assets/06687491-8729-4bbe-80af-5875a1d2f6f1)

```
sns.scatterplot(data=af)
```
![421784307-ba8d6d82-0495-46f2-add0-ca203d73a0da](https://github.com/user-attachments/assets/b9dda1ac-3cf9-4c45-b8e5-73e368893873)

```
q1=af.quantile(0.75)
q2=af.quantile(0.5)
q3=af.quantile(0.25)
irq=q3-q1
irq
```
![421784451-35d5583c-4818-463c-89ef-12a4fed74617](https://github.com/user-attachments/assets/a0aad316-511b-41e7-a0ed-51eac0c58332)

```
Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR
```
![421784576-8c3c322e-2b95-4906-841d-5bb6ff6376c0](https://github.com/user-attachments/assets/b034c723-06a0-4b6f-ad25-222cfa840d5b)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
```
![421784698-1a342717-0c1d-4c85-855b-943733a3adf5](https://github.com/user-attachments/assets/f59af5ff-63ba-4a43-a962-39d0b82fd2aa)
```
upper_bound
```
![421784814-676930ff-0f77-49cf-8e5c-1b5b18ac6df5](https://github.com/user-attachments/assets/9cb4f5e4-390c-4eb5-9fd2-614aeab597a7)

```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
outliers
```
![421784962-6d04c995-d216-48c3-bde6-72c16a5b0e31](https://github.com/user-attachments/assets/ba07593c-95cb-49e8-b752-02bb3f93b126)

```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
```
![421785125-7758e394-6bf4-4576-b782-1d135f727373](https://github.com/user-attachments/assets/93ab3ad9-aeda-4e51-b6e1-6c785a6e0b05)

```
af.dropna()
```
![421785338-61283903-a260-4c2b-a832-f5d194e8f54a](https://github.com/user-attachments/assets/7fc3030b-f443-4fbe-8cf2-ee79de10c06c)

```
sns.boxplot(data=af)
```
![421785484-a21d3f93-56a8-4fa4-b653-590647072cb7](https://github.com/user-attachments/assets/de520a84-8322-4a54-9efa-b35f1fabc2bb)

```
sns.scatterplot(data=af)
```
![421785617-511edcc2-145a-4c4f-9147-92ae79242d43](https://github.com/user-attachments/assets/07782ffb-b652-4d4f-97ef-41dbea5a7427)

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
```
```
data = [1, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48, 51, 54, 57, 60,
        63, 66, 69, 72, 75, 78, 81, 84, 87, 90, 93, 96, 99, 158]
df = pd.DataFrame(data,columns=['Value'])
df
```
![421787746-df6e322f-b4fc-49ff-909d-cbc0c2b9913f](https://github.com/user-attachments/assets/d587c1a6-23e5-417c-992b-cd8a87df00cb)

```
sns.boxplot(data=df)
plt.show()
```
![421787905-506ce79b-a0eb-4370-bef3-2e2e85dc5122](https://github.com/user-attachments/assets/12d77a3a-efab-4e50-beb1-eed32f6df16f)
```
z_scores = np.abs(stats.zscore(df['Value']))
outliers = df[z_scores > 3]
print( outliers['Value'].tolist())
```
![421788000-d6ceb438-a835-445c-a5bb-aa50e3565275](https://github.com/user-attachments/assets/3954d745-d688-47b2-819e-8e83cb987296)
```
df_clean = df[z_scores <= 3]
```
```
sns.boxplot(data=df_clean)  
plt.show()
```
![421789082-990cfa62-32a5-44a1-8277-ec4f68b63f57](https://github.com/user-attachments/assets/c7a8522e-202e-4d04-9aed-77f7164a409b)

# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
