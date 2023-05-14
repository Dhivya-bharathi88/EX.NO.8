# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
import pandas as pd

import numpy as np

import seaborn as sns

import matplotlib.pyplot as plt

from google.colab import files

uploaded = files.upload()

df=pd.read_csv("SuperStore.csv",encoding='unicode_escape')

df

# Data Cleaning Process:
df.describe()

df.info()

df.drop('Row ID',axis=1,inplace=True)

df.drop('Order ID',axis=1,inplace=True)

df.drop('Customer ID',axis=1,inplace=True)

df.drop('Customer Name',axis=1,inplace=True)

df.drop('Country',axis=1,inplace=True)

df.drop('Postal Code',axis=1,inplace=True)

df.drop('Product ID',axis=1,inplace=True)

df.drop('Product Name',axis=1,inplace=True)

df.drop('Order Date',axis=1,inplace=True)

df.drop('Ship Date',axis=1,inplace=True)

df

df.isnull().sum()

# Segment has Highest sales:
sns.barplot(x="Segment",y="Sales",data=df)

plt.xticks(rotation = 90)

plt.show()

# City has Highest profit:
plt.figure(figsize=(30,8))

states=df1.loc[:,["City","Profit"]]

states=states.groupby(by=["City"]).sum().sort_values(by="Profit")

sns.barplot(x=states.index,y="Profit",data=states)

plt.xticks(rotation = 90)

plt.xlabel=("City")

plt.ylabel=("Profit")

plt.show()

# Ship mode is profitable:
sns.barplot(x="Ship Mode",y="Profit",data=df)

plt.show()

# Sales of the product based on Region:
states=df.loc[:,["Region","Sales"]]

states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")

sns.barplot(x=states.index,y="Sales",data=states)

plt.xticks(rotation = 90)

plt.xlabel=("Region")

plt.ylabel=("Sales")

plt.show()

# Relation between sales and profit:
sns.lineplot(x="Sales",y="Profit",data=df,hue="Region",style="Region",markers=["o","<"])

# Relation between sales and profit based on Segment:
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('Segment')

ax.set_ylabel('Value')

ax.legend()

plt.show()

# Relation between sales and profit based on City:
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('City')

ax.set_ylabel('Value')

ax.legend()

plt.xticks(rotation = 90)

plt.show()

# Relation between sales and profit based on States:
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()

fig, ax = plt.subplots()

ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')

ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')

ax.set_xlabel('State')

ax.set_ylabel('Value')

ax.legend()

plt.xticks(rotation = 90)

plt.show()

# Relation between sales and profit based on Segment and Ship Mode:
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])

fig, ax = plt.subplots()

pivot_data.plot(kind='bar', ax=ax)

ax.set_xlabel('Segment')

ax.set_ylabel('Value')

plt.legend(title='Ship Mode')

plt.show()

# Relation between sales and profit based on Segment , Ship Mode and Region:
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()

pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])

sns.set_style("whitegrid")

sns.set_palette("Set1")

pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))

plt.legend(title='Region')

plt.show()

# OUTPUT:
# Data Cleaning Process:
![Screenshot (196)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/cb4ea919-0239-45eb-bd4a-53d42257ff78)
![Screenshot (197)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/07fa5034-cb14-4a75-96c9-df53c2ea5ad2)
![Screenshot (198)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/e2661a7e-d3ba-4a78-9462-cc5c616cf4f9)
![Screenshot (199)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/7c33b8fc-9dc9-4993-a2b0-5e3c4406ec75)
![Screenshot (200)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/f169789a-5d6a-42b0-8656-af185e015210)
# Segment has Highest sales:
![Screenshot (201)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/1696c411-d446-427e-99b0-6f537a9bff65)
# City has Highest profit:
![Screenshot (202)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/ae2c382b-b8a6-476d-8442-702880bef309)
# Ship mode is profitable:
![Screenshot (203)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/60ecc6df-c3b3-41a6-9141-d8f2a9e7d980)
# Sales of the product based on Region:
![Screenshot (204)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/a2e53377-ea2c-448c-acf5-15d393e51f8e)
# Relation between sales and profit:
![Screenshot (205)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/73198633-d7c5-4265-87e8-7fb2564b90ed)
# Relation between sales and profit based on Segment:
![Screenshot (206)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/31a1622b-481f-4bf4-9f94-886b2e64fa56)
# Relation between sales and profit based on City:
![Screenshot (207)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/a3c111db-d4ae-4f14-890b-5c0172e419d6)
# Relation between sales and profit based on States:
![Screenshot (208)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/c270011d-f8cf-4907-82ff-899952c19559)
# Relation between sales and profit based on Segment and Ship Mode:
![Screenshot (209)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/f7a328bc-7c08-472b-92e0-f70989462804)
# Relation between sales and profit based on Segment , Ship Mode and Region:
![Screenshot (210)](https://github.com/Dhivya-bharathi88/EX.NO.8/assets/128019999/e6d5cc42-c157-42c3-9211-110691939eee)
# RESULT:
Thus the Data Visualization techniques was performed for the given dataset and output was verified successfully.
