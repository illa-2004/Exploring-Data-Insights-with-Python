# Exploring-Data-Insights-with-Python
#This task involves performing exploratory data analysis on a dataset.
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
df = pd.read_csv('/content/tips - tips.csv')

# Inspect the data
print(df.head())
print(df.columns)  # Check column names
print(df.info())
print(df.describe())

# Univariate Analysis
# Histograms for numerical features
df.hist(bins=30, figsize=(15, 10))
plt.show()

# Box plots for detecting outliers
plt.figure(figsize=(10, 6))
sns.boxplot(data=df, x='tip')  
plt.show()

# Bar plots for categorical features
plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='time')  
plt.show()

# Correlation Matrix
# Select only numerical columns
numerical_df = df.select_dtypes(include=['float64', 'int64'])
correlation_matrix = numerical_df.corr()
plt.figure(figsize=(12, 8))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f')
plt.show()

# Pair Plot
# Select only numerical columns for pair plot
sns.pairplot(numerical_df)
plt.show()

# Violin Plot
plt.figure(figsize=(10, 6))
sns.violinplot(data=df, x='time', y='tip') 
plt.show()
