# Python_Project
Student Result Analysis

By this project, we will get idea about the student results based on gender, their parent's education, etc.
Maths subject is toughest among the other subjects.

import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
df=pd.read_csv('Student_Result_Analysis.csv')
print(df.head())
print(df.describe())
print(df.info())
print(df.isnull().sum())

Drop Unnamed Column
df=df.drop("Unnamed: 0",axis=1)
print(df)

Gender Distribution
plt.figure(figsize=(5,5))
ax = sns.countplot(data=df,x="Gender")
ax.bar_label(ax.containers[0])
plt.title("Gender Distribution")
plt.show()

#Conclusion: The no of females in the data is more than the no of males

gb=df.groupby("ParentEduc").agg({"MathScore":"mean","ReadingScore":"mean","WritingScore":"mean"})
print(gb)

plt.figure(figsize=(4,4))
sns.heatmap(gb,annot=True)
plt.title("Relationship between Parent's Education & Student's Score")
plt.show()

#Conclusion: Education of the parent have a good impact on their student's score.

gb1=df.groupby("ParentMaritalStatus").agg({"MathScore":"mean","ReadingScore":"mean","WritingScore":"mean"})
print(gb1)

plt.figure(figsize=(4,4))
sns.heatmap(gb1,annot=True)
plt.title("Relationship between Parent's Marital Status & Student's Score")
plt.show()

#Conclusion: There is no/neglible impact on the student's score due to their parent's marital status.

sns.boxplot(data=df,x="MathScore")
plt.show()

sns.boxplot(data=df,x="ReadingScore")
plt.show()

sns.boxplot(data=df,x="WritingScore")
plt.show()

#Conclusion : Maths is comparatively difficult subjects for the students to get the good marks.

print(df["EthnicGroup"].unique())

Distribution of Ethnic Groups

groupA = df.loc[(df["EthnicGroup"]=="group A")].count()

groupB = df.loc[(df["EthnicGroup"]=="group B")].count()

groupC = df.loc[(df["EthnicGroup"]=="group C")].count()

groupD = df.loc[(df["EthnicGroup"]=="group D")].count()

groupE = df.loc[(df["EthnicGroup"]=="group E")].count()
print(groupA["EthnicGroup"])
l=["group A", "group B", "group C","group D","group E"]
mylist = [groupA["EthnicGroup"], groupB["EthnicGroup"], groupC["EthnicGroup"],groupD["EthnicGroup"], groupE["EthnicGroup"]]
print(mylist)
plt.pie(mylist, labels=l, autopct="%0.2f%%")
plt.title("Distribution of Ethnic Groups")
plt.show()

#Conclusion : Group C - Ethnic Groups is highest.

ax= sns.countplot(data=df, x= "EthnicGroup")
print(ax.bar_label(ax.containers[0]))
plt.show()
