
# 🍕 **Pizza Hut Sales Analysis** 🍕

![Pizza Hut Logo](PizzaHut_img.png)

**A Comprehensive Analysis of Pizza Hut's Sales Data**

Welcome to the **Pizza Hut Sales Analysis** repository! This project involves a detailed analysis of Pizza Hut's sales data, helping uncover key insights into sales trends, best-selling products, regional performance, and much more. It provides actionable insights for business strategies, marketing decisions, and customer satisfaction.

## 🚀 Project Overview

The goal of this project is to analyze the sales data of Pizza Hut to uncover trends and gain valuable insights, including:
- **Sales Trends**: How sales fluctuate over time.
- **Top Selling Products**: Identifying the best-performing menu items.
- **Regional Sales**: Understanding the performance across different regions.
- **Promotional Impact**: Exploring how discounts and promotions affect sales.
- **Customer Purchase Patterns**: Understanding customer preferences and behaviors.

By analyzing this data, we aim to offer insights that can help Pizza Hut optimize operations, marketing strategies, and product offerings.

## 📊 Dataset

The dataset used for this analysis contains various attributes of the sales, including:
- **OrderID**: Unique identifier for each order.
- **MenuItem**: Name of the item ordered (pizza, sides, etc.).
- **Quantity**: Number of items ordered.
- **Price**: Price of the individual item.
- **Discount**: Discount applied to the item.
- **Sales**: Total sales for the item (Price * Quantity - Discount).
- **OrderDate**: Date when the order was placed.
- **Region**: The geographical region where the order was made.

## 🛠️ Tools & Technologies

This project utilizes the following tools and technologies:
- **Python**: Programming language for data manipulation and analysis.
- **Pandas**: For data wrangling and manipulation.
- **Matplotlib & Seaborn**: For creating engaging visualizations and charts.
- **Jupyter Notebooks**: Interactive platform to analyze and visualize data.
- **NumPy**: For numerical operations.

## 🔧 Installation

To run this project locally, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/ShubhamMvernekar/PizzaHut-Sales-Analysis.git
   cd PizzaHut-Sales-Analysis
   ```

2. **Install dependencies**:
   - Create a virtual environment (optional but recommended):
     ```bash
     python -m venv venv
     source venv/bin/activate  # On Windows use `venv\Scripts\activate`
     ```
   - Install the required libraries:
     ```bash
     pip install -r requirements.txt
     ```

3. **Run Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

4. **Explore the analysis** in the Jupyter notebook to uncover insights from the data.

## 📂 Project Structure

This is how the project is organized:
- `data/`: Contains the raw dataset for analysis.
- `notebooks/`: Jupyter notebooks with data exploration, analysis, and visualizations.
- `requirements.txt`: A list of Python dependencies.
- `README.md`: This file, explaining the project.

## 🔍 Key Insights & Analysis

### 1. **Sales Trends Over Time**
By analyzing the sales over time, we can identify peak sales periods, seasonal variations, and overall sales growth.

#### Example Visualization: Sales Trends Over Time
![Sales Trend](https://via.placeholder.com/600x300?text=Sales+Trend+Over+Time)  
*This line chart shows the sales growth over the months.*

#### Example Code:
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the data
df = pd.read_csv('data/pizza_sales.csv')

# Convert OrderDate to datetime
df['OrderDate'] = pd.to_datetime(df['OrderDate'])

# Group sales by Month
df['YearMonth'] = df['OrderDate'].dt.to_period('M')
monthly_sales = df.groupby('YearMonth')['Sales'].sum()

# Plotting Sales Trend
plt.figure(figsize=(10, 6))
monthly_sales.plot(kind='line', marker='o', color='tomato')
plt.title('Monthly Sales Trend for Pizza Hut')
plt.xlabel('Month')
plt.ylabel('Sales ($)')
plt.xticks(rotation=45)
plt.grid(True)
plt.show()
```

### 2. **Top Selling Menu Items**
Understanding which menu items are the most popular allows for better inventory management and marketing decisions.

#### Example Visualization: Top Selling Menu Items
![Top Selling Pizza](https://via.placeholder.com/600x300?text=Top+Selling+Pizza)  
*Bar chart showing the top-selling pizzas at Pizza Hut.*

#### Example Code:
```python
top_items = df.groupby('MenuItem')['Sales'].sum().sort_values(ascending=False).head(10)

# Plotting the top 10 selling menu items
top_items.plot(kind='barh', color='cornflowerblue', title='Top 10 Best-Selling Menu Items')
plt.xlabel('Total Sales ($)')
plt.ylabel('Menu Items')
plt.show()
```

### 3. **Regional Sales Distribution**
This analysis shows the performance of Pizza Hut across different regions, which is valuable for targeted promotions.

#### Example Visualization: Sales by Region
![Sales by Region](https://via.placeholder.com/600x300?text=Sales+by+Region)  
*Pie chart illustrating sales distribution across regions.*

#### Example Code:
```python
region_sales = df.groupby('Region')['Sales'].sum()

# Plotting the regional sales distribution
region_sales.plot(kind='pie', autopct='%1.1f%%', figsize=(8, 8), title="Sales Distribution by Region")
plt.ylabel('')
plt.show()
```

### 4. **Promotional Effectiveness**
Analyzing the impact of promotions and discounts on sales can help optimize pricing strategies.

#### Example Visualization: Effect of Discounts on Sales
![Discount Impact](https://via.placeholder.com/600x300?text=Discount+Impact)  
*Bar chart comparing sales with and without discounts.*

#### Example Code:
```python
# Filter data for orders with discounts
discounted_sales = df[df['Discount'] > 0]

# Plotting sales comparison for discounted and non-discounted items
plt.figure(figsize=(10, 6))
sales_comparison = [df[df['Discount'] == 0]['Sales'].sum(), discounted_sales['Sales'].sum()]
plt.bar(['Non-Discounted', 'Discounted'], sales_comparison, color=['skyblue', 'orange'])
plt.title('Sales Comparison: Discounted vs Non-Discounted')
plt.ylabel('Total Sales ($)')
plt.show()
```

## 🍕 Sample Visualizations

### **Pizza Sales Overview**
![Pizza Sales Overview](https://via.placeholder.com/600x300?text=Pizza+Sales+Overview)  
*Visualizing overall pizza sales trends.*

### **Top Pizza by Region**
![Top Pizza by Region](https://via.placeholder.com/600x300?text=Top+Pizza+by+Region)  
*Bar chart showing the most popular pizzas in each region.*

## 🤝 Contributing

Contributions are always welcome! If you'd like to enhance this project, you can:
- Add new visualizations or insights.
- Implement machine learning models to predict future sales.
- Improve data wrangling techniques or the analysis process.

Please fork this repository, create a branch, and submit a pull request. If you find any bugs or have suggestions, feel free to open an issue.
