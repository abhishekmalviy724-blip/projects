# project
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
Data=pd.read_csv("real_2013_air (1).csv")
print(Data.shape)
print(Data.info())
print(Data.head(5))
print(Data.columns)

print(Data.isnull().sum()/len(Data)*100)
print(Data.fillna(Data["PM 2.5"].median()))

print(Data["PM 2.5"].nlargest(5))
print(Data["PM 2.5"].nunique())

Data["NewColum"]=np.where(Data["PM 2.5"]>100,"High", np.where(Data["PM 2.5"]>50,"Medium","Low"))
Data.to_csv("real_2013_air (1).csv",index=False)
print("Done")

Data["T"].corr(Data["H"])
graphh=Data.corr(numeric_only=True)
sns.heatmap(data=graphh,annot=True)
plt.show()

plt.hist(x="PM 2.5")
plt.xlabel("PM 2.5")
plt.ylabel("Freqancy")
plt.title("PM 2.5 Distribution")
plt.show()

sns.boxplot(x=Data["PM 2.5"])
plt.xlabel("PM 2.5")
plt.ylabel("Freqancy")
plt.title("PM 2.5 Distribution")
plt.grid()
plt.show()

sns.scatterplot(x=Data["T"],y=Data["PM 2.5"])
plt.xlabel("Temperature")
plt.ylabel("PM 2.5")
plt.title("PM 2.5 Distribution")
plt.grid()
plt.show()

sns.scatterplot(x=Data["H"],y=Data["PM 2.5"])
plt.xlabel("HUmidity")
plt.ylabel("PM 2.5")
plt.title("PM 2.5 Distribution")
plt.grid()
plt.show()

print(Data.groupby("T")["PM 2.5"].mean())
print(Data.groupby("H")["PM 2.5"].agg(["mean","max"]))

print(Data["NewColum"].value_counts())
print(Data["PM 2.5"].nlargest(5))

print(len(Data))
print(Data["PM 2.5"].agg(["mean","std","max","min"]))
print(Data[(Data["NewColum"]=="High")].count())
print(Data[(Data["NewColum"]=="Medium")].count())
print(Data[(Data["NewColum"]=="Low")].count())

sns.histplot(x=Data["PM 2.5"])
plt.title("PM 2.5 Distribution")
plt.show()

sns.countplot(x=Data["NewColum"])
plt.title("PM 2.5 Distribution")
plt.show()

sns.scatterplot(x=Data["T"], y=Data["PM 2.5"])
plt.title("PM 2.5 Distribution")
plt.xlabel("Temprature")
plt.grid()
plt.show()

graph = Data.corr(numeric_only=True)
sns.heatmap(graph,annot=True)
plt.title("PM 2.5 Distribution")
plt.xlabel("Temprature")
plt.grid()
plt.show()
