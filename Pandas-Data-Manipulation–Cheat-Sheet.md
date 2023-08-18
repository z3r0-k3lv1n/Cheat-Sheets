# Pandas Cheat Sheet

## Import Pandas

```
#!/bin/env python3

import pandas as pd
```

---
## Create DataFrames

```
# From a dictionary
data = {'Column1': [value1, value2, value3],
        'Column2': [value4, value5, value6]}
df = pd.DataFrame(data)

# From a CSV file
df = pd.read_csv('file.csv')

# From a SQL database
from sqlalchemy import create_engine
engine = create_engine('sqlite:///database.db')
df = pd.read_sql_query('SELECT * FROM table', engine)
```

---
## Basic Operations
```
df.head()          # Display first 5 rows
df.tail()          # Display last 5 rows
df.info()          # Summary of DataFrame
df.describe()      # Summary statistics
df.shape           # Number of rows and columns
df.columns         # Column names
df.index           # Row index
```

---
## Data Selection
```
df['Column']                 # Select a column
df[['Column1', 'Column2']]   # Select multiple columns
df.loc[row_label]            # Select by label
df.iloc[row_index]           # Select by index
df.iloc[start:end]           # Slice rows
df.query('Condition')        # Select by condition
```

---
## Data Cleaning
```
df.drop(columns=['Column'])             # Drop column
df.dropna()                            # Drop rows with NaN
df.fillna(value)                       # Fill NaN with a value
df.replace(old, new)                   # Replace values
df.duplicated()                        # Find duplicates
df.drop_duplicates()                   # Drop duplicates
```

---
## Data Manipulation
```
df.sort_values('Column')                # Sort by column
df.groupby('Column').mean()             # Group by column and calculate mean
df.pivot_table(values, index, columns)  # Create pivot table
df.merge(other_df, on='Column')         # Merge DataFrames
df.join(other_df)                       # Join DataFrames
```

---
## Data Analysis
```
df['Column'].value_counts()     # Count unique values
df['Column'].unique()           # Get unique values
df['Column'].nunique()          # Count unique values
df.groupby('Column').sum()      # Group by and calculate sum
df.corr()                       # Correlation matrix
df.crosstab(df['Col1'], df['Col2'])  # Crosstab
```

---
## Data Visualisation
```
import matplotlib.pyplot as plt
import seaborn as sns

df['Column'].plot(kind='hist')                # Histogram
df.plot(x='Col1', y='Col2', kind='scatter')   # Scatter plot
sns.heatmap(df.corr(), annot=True)            # Correlation heatmap
```

---
## Saving Data
```
df.to_csv('file.csv', index=False)         # Save as CSV
df.to_excel('file.xlsx', index=False)      # Save as Excel
df.to_sql('table', engine, index=False)    # Save to SQL database
```

> Remember to replace the placeholders like value1, value2, file.csv, database.db, etc., with actual values relevant to your dataset. Happy coding!

---
Feel free to send a pull request into your GitHub repository for a comprehensive Pandas Cheat Sheet.


