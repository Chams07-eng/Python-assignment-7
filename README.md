# Python-assignment-7
# Task 1: Load and Explore the Dataset

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = sns.load_dataset('iris')

# Display first few rows
print("First 5 rows of the dataset:")
print(df.head())

# Check data types and structure
print("\nDataset Information:")
print(df.info())

# Check for missing values
print("\nMissing values in the dataset:")
print(df.isnull().sum())

# No missing values to clean, but in general:
# df.dropna(inplace=True) or df.fillna(method='ffill', inplace=True)



# Task 2: Basic Data Analysis

# Basic statistics
print("\nStatistical Summary:")
print(df.describe())

# Grouping by species and computing mean
print("\nMean of features grouped by species:")
print(df.groupby('species').mean())

# Observations
print("\nFindings:")
print("- Setosa has smaller sepal and petal dimensions on average.")
print("- Petal length and width are highly indicative of species.")
print("- The dataset is clean and well-balanced across the three species.")


# Task 3: Data Visualization

# 1. Line chart – simulate trend using cumulative sum for visualization purposes
df['index'] = df.index
df_sorted = df.sort_valu# 3. Histogram – distribution of sepal width
plt.hist(df['sepal_width'], bins=10, color='orange', edgecolor='black')
plt.title('Distribution of Sepal Width')
plt.xlabel('Sepal Width')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()
es(by='index')
df_sorted['cumulative_petal_length'] = df_sorted['petal_length'].cumsum()

plt.figure(figsize=(10, 5))
plt.plot(df_sorted['index'], df_sorted['cumulative_petal_length'], color='green')
plt.title('Cumulative Petal Length Over Index')
plt.xlabel('Index')
plt.ylabel('Cumulative Petal Length')
plt.grid(True)
plt.show()


# 2. Bar chart – average petal length per species
species_avg = df.groupby('species')['petal_length'].mean()

species_avg.plot(kind='bar', color='skyblue')
plt.title('Average Petal Length per Species')
plt.xlabel('Species')
plt.ylabel('Average Petal Length')
plt.xticks(rotation=0)
plt.grid(axis='y')
plt.show()


# 3. Histogram – distribution of sepal width
plt.hist(df['sepal_width'], bins=10, color='orange', edgecolor='black')
plt.title('Distribution of Sepal Width')
plt.xlabel('Sepal Width')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()


# 4. Scatter plot – sepal length vs petal length
sns.scatterplot(data=df, x='sepal_length', y='petal_length', hue='species')
plt.title('Sepal Length vs Petal Length by Species')
plt.xlabel('Sepal Length')
plt.ylabel('Petal Length')
plt.legend(title='Species')
plt.grid(True)
plt.show()

print("""
Observations Summary:
- No missing values were found.
- Setosa species has significantly shorter petals than Versicolor and Virginica.
- Petal length and petal width are strong indicators for classifying species.
- Distribution of sepal width shows moderate spread and some skewness.
- Scatter plots confirm that different species form distinguishable clusters.
""")



