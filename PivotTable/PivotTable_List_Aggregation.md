If you want to create a pivot table that includes all the values without aggregating them into a single number, you'd typically use a different approach, as pivot tables in pandas are primarily designed to summarize data through aggregation.

However, if your goal is to display all values associated with specific combinations of columns (in this case, EIN and Year), you might consider using some alternative techniques. Here are a few approaches you can take:

**1. Using groupby and agg(list)**

This method allows you to group the data and aggregate it into lists instead of summing or averaging. Here's how you could do it.

**Example Scenario**

Let's take the same sales data as before but focus on retaining all reported sales amounts for each combination of EIN and Year.

**DataFrame Example**

| **Year** | **EIN** | **Sales** |
| --- | --- | --- |
| 2021 | 101 | 100 |
| 2021 | 101 | 150 |
| 2021 | 102 | 200 |
| 2021 | 102 | 100 |
| 2022 | 101 | 300 |
| 2022 | 102 | 400 |
| 2022 | 102 | 500 |

**Code Snippet**

Here's how you can achieve this using groupby combined with agg(list):

import pandas as pd

\# Sample DataFrame

data = {

'Year': \[2021, 2021, 2021, 2021, 2022, 2022, 2022\],

'EIN': \[101, 101, 102, 102, 101, 102, 102\],

'Sales': \[100, 150, 200, 100, 300, 400, 500\]

}

df = pd.DataFrame(data)

\# Grouping the DataFrame and aggregating sales into lists

sales_summary = df.groupby(\['EIN', 'Year'\])\['Sales'\].agg(list).reset_index()

\# Display the resulting DataFrame

print(sales_summary)

**Expected Output**

When you run the code snippet above, the expected output will look like this:

| **EIN** | **Year** | **Sales** |
| --- | --- | --- |
| 101 | 2021 | \[100, 150\] |
| 101 | 2022 | \[300\] |
| 102 | 2021 | \[200, 100\] |
| 102 | 2022 | \[400, 500\] |

**2. Using stack for More Visibility**

If you want a more detailed view and are fine with a different format, you can consider using the melt() function, followed by some restructuring. However, this may not suit the "pivot table" format you're looking for but will keep each entry visible.

**3. Using pivot for Values Without Aggregation**

If you must use a pivot-like approach but want all values without aggregation, you can reshuffle your DataFrame using pivot, provided your data doesn't create duplicates (which would lead to errors).

**Summary**

- **Aggregation in Pivot Tables**: Standard pivot tables require aggregation (like sum, mean, etc.), which is useful for summarizing data but loses individual data points.
- **Grouping with List Aggregation**: Using groupby with agg(list) allows you to retain all values in a structured manner.
