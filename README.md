# Applied_Data_Science
#Import Libraries


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import datetime

#Read the csv file

my_data = pd.read_csv("BigmacPrice.csv")

my_data 
#to function the header
my_data.head()

#Exploratory Data Analysis

my_data.info()

my_data.describe()

my_data.isnull().sum()

#Selecting 5 Countries for multiple line plot

group_argentina = my_data[(my_data['name'] == "Argentina")]
group_australia = my_data[(my_data['name'] == "Australia")] 
group_brazil = my_data[my_data['name'] == "Brazil"]
group_britain = my_data[my_data['name'] == "Britain"]
group_canada = my_data[my_data['name'] == "Canada"]

#Extracting year from the date for 5 Countries

group_argentina['year'] = pd.to_datetime(group_argentina['date']).dt.year
group_australia['year'] = pd.to_datetime(group_australia['date']).dt.year
group_brazil['year'] = pd.to_datetime(group_brazil['date']).dt.year
group_britain['year'] = pd.to_datetime(group_britain['date']).dt.year
group_canada['year'] = pd.to_datetime(group_canada['date']).dt.year

#TO Function Multi line plot

plt.plot(group_argentina['year'], group_argentina['dollar_price'], label="Argentina")
plt.plot(group_australia['year'], group_australia['dollar_price'], label="Australia")
plt.plot(group_brazil['year'], group_brazil['dollar_price'], label="Brazil")
plt.plot(group_britain['year'], group_britain['dollar_price'], label="Britain")
plt.plot(group_canada['year'], group_canada['dollar_price'], label="Chile")
plt.legend()
plt.ylabel('Dollar Price')
plt.xlabel("Years")
plt.title("Big mac Year Wise Dollar Price for 5 Countries", fontsize="15")
plt.savefig("Bigmac year 5 countries.png")
plt.show()

#Extracting year from date in original dataset

my_data['year'] = pd.to_datetime(my_data['date']).dt.year

my_data.head()

#Barplot for dollar price

plt.bar(my_data['year'], my_data['dollar_price'], color='b', label='dollar price')
plt.title(label="Big MacYear wise dollar price")
plt.ylabel('Dollar Price')
plt.xlabel("Years")
plt.legend()
plt.savefig("Bigmac dollar price barplot.png")
plt.show()


#Scatterplot for local price

plt.scatter(my_data['year'], my_data['dollar_price'] ,color='b', label='Local price')
plt.title(label="Big MacYear wise local price")
plt.ylabel('Local Price')
plt.xlabel("Years")
plt.legend()
plt.savefig("Bigmac local price scatterplot.png")
plt.show()


