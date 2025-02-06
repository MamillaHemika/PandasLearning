Let's consider a scenario where we have sales data that includes multiple entries for the same EIN and year, with different sales amounts. In this case, we might want to aggregate the sales data in our pivot table using a specific mathematical operation, such as summing or averaging the sales amounts for each unique combination of EIN and year.

**Example Scenario**

Imagine we have the following sales data:

| **Year** | **EIN** | **Sales** |
| --- | --- | --- |
| 2021 | 101 | 100 |
| 2021 | 101 | 150 |
| 2021 | 102 | 200 |
| 2021 | 102 | 100 |
| 2022 | 101 | 300 |
| 2022 | 102 | 400 |
| 2022 | 102 | 500 |

In this case, we want to create a pivot table that shows the total sales for each EIN for each year.

**Code Snippet**

Here's how you can create a pivot table that sums the sales for each EIN and year.

import pandas as pd

\# Sample DataFrame

data = {

'Year': \[2021, 2021, 2021, 2021, 2022, 2022, 2022\],

'EIN': \[101, 101, 102, 102, 101, 102, 102\],

'Sales': \[100, 150, 200, 100, 300, 400, 500\]

}

df = pd.DataFrame(data)

\# Create the pivot table with aggregation

sales_summary = df.pivot_table(index='EIN', columns='Year', values='Sales', aggfunc='sum').reset_index()

\# Display the resulting pivot table

print(sales_summary)

**Expected Output**

When you run the code snippet above, the expected output from the pivot table will look like this:

| **EIN** | **2021** | **2022** |
| --- | --- | --- |
| 101 | 250 | 300 |
| 102 | 300 | 900 |

**Explanation of the Output**

- **EIN 101**:
  - In 2021, the total sales are **250** (100 + 150).
  - In 2022, the total sales are **300**.
- **EIN 102**:
  - In 2021, the total sales are **300** (200 + 100).
  - In 2022, the total sales are **900** (400 + 500).

**Summary**

In this example, the pivot table effectively aggregates the Sales data across years and EINs using the sum function as the differentiator. This allows you to clearly see total sales for each company over different years. You could easily modify the aggfunc parameter to use other aggregation methods, such as 'mean', 'max', or even custom functions, depending on your analytical needs.
