# pandas-and-visualising-results
1) loads
   import pandas as pd

# Load the dataset (assuming you have a sales_data.csv file)
df = pd.read_csv('sales_data.csv')

# Display the first few rows of the dataset to inspect
print("First few rows of the dataset:")
print(df.head())

# Check the structure of the dataset
print("\nDataset information (data types and non-null counts):")
print(df.info())

# Check for missing values
print("\nMissing values in each column:")
print(df.isnull().sum())

# Clean the dataset by filling or dropping missing values
# Option 1: Drop rows with missing values
df_cleaned_drop = df.dropna()

# Option 2: Fill missing values with a specific value (e.g., fill with the mean of the column)
df_cleaned_fill = df.fillna(df.mean())

# Show the cleaned data (after drop or fill)
print("\nCleaned dataset (after filling or dropping missing values):")
print(df_cleaned_fill.head())
@BASIC DATA ANALASYS
import pandas as pd

# Load the dataset (assuming you have a sales_data.csv file)
df = pd.read_csv('sales_data.csv')

# Step 1: Compute basic statistics of the numerical columns
print("Basic statistics of the numerical columns:")
print(df.describe())

# Step 2: Perform groupings on a categorical column (e.g., 'region')
# Assuming there's a 'region' column (categorical) and 'sales' column (numerical)
grouped_by_region = df.groupby('region')['sales'].mean()

# Display the mean sales for each region
print("\nMean sales by region:")
print(grouped_by_region)

# Step 3: Identify patterns or interesting findings
# You could compare different regions, or if you have more data, look at other stats (e.g., median, sum, etc.)
@DATA VISUALISATION
Sure! Below is an example of how you can create the four different types of visualizations using **matplotlib** and **seaborn** in Python:

### Required Libraries:

First, make sure you have the necessary libraries installed:

```bash
pip install matplotlib seaborn pandas
```

### Step-by-step Visualization Creation:

Let's assume you have a dataset that includes `sales_data.csv`, with columns like `date`, `species`, `sales`, `sepal_length`, `petal_length`, etc.

#### 1. **Line Chart (Time-Series of Sales Data)**:
A line chart is great for visualizing trends over time.

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('sales_data.csv')

# Convert the 'date' column to datetime format (if it's not already)
df['date'] = pd.to_datetime(df['date'])

# Group sales by date and sum the values (if there are multiple entries per day)
df_daily_sales = df.groupby('date')['sales'].sum()

# Line chart to show sales trends over time
plt.figure(figsize=(10, 6))
plt.plot(df_daily_sales.index, df_daily_sales.values, color='blue', marker='o', linestyle='-', linewidth=2)
plt.title('Sales Trends Over Time')
plt.xlabel('Date')
plt.ylabel('Total Sales')
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

#### 2. **Bar Chart (Comparison of Numerical Value Across Categories)**:
A bar chart is useful for comparing values across categories (e.g., average sales by region or average petal length by species).

```python
import seaborn as sns

# Assuming 'region' and 'sales' columns exist
plt.figure(figsize=(10, 6))
sns.barplot(x='region', y='sales', data=df, palette='viridis')
plt.title('Average Sales by Region')
plt.xlabel('Region')
plt.ylabel('Average Sales')
plt.show()
```

#### 3. **Histogram (Distribution of a Numerical Column)**:
A histogram helps understand the distribution of values in a numerical column.

```python
# Plot histogram for sales data to understand distribution
plt.figure(figsize=(10, 6))
plt.hist(df['sales'], bins=10, color='skyblue', edgecolor='black')
plt.title('Distribution of Sales')
plt.xlabel('Sales')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()
```

#### 4. **Scatter Plot (Relationship Between Two Numerical Columns)**:
A scatter plot is useful for visualizing relationships between two numerical variables.

```python
# Assuming 'sepal_length' and 'petal_length' columns exist
plt.figure(figsize=(10, 6))
plt.scatter(df['sepal_length'], df['petal_length'], alpha=0.7, c='orange')
plt.title('Relationship Between Sepal Length and Petal Length')
plt.xlabel('Sepal Length')
plt.ylabel('Petal Length')
plt.grid(True)
plt.show()
```

### Customization:

- **Titles**: Each plot has a title set using `plt.title()`.
- **Axis Labels**: Use `plt.xlabel()` and `plt.ylabel()` to set labels for the x and y axes.
- **Legends**: In some cases, you can add legends using `plt.legend()`, especially for multiple lines or data points in one plot.
- **Grid**: `plt.grid(True)` adds a grid to make the plot easier to read.

### Example Output for Each Plot:

1. **Line Chart**: Shows the sales trend over time, with the x-axis representing dates and the y-axis representing sales.
2. **Bar Chart**: Compares the average sales across different regions.
3. **Histogram**: Displays the distribution of sales, showing how frequently sales fall into different bins.
4. **Scatter Plot**: Visualizes how `sepal_length` and `petal_length` relate to each other, helping to spot any correlation.

### Customization for Specific Requirements:
- For **color schemes**, you can change the palette in seaborn (`palette='viridis'`), or specify color codes directly.
- **Logarithmic scales**: If data spans a large range, you might want to use logarithmic scaling on one of the axes (`plt.yscale('log')`).

These visualizations will give you a good understanding of trends, relationships, and distributions in your data. Let me know if you need further customization or additional visualizations!
