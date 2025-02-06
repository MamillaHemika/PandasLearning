The iterrows() function in pandas is a method used to iterate over the rows of a DataFrame. This function is commonly used when you need to perform operations on each row, allowing for row-wise processing of data.

**Overview of iterrows()**

- **Purpose**: The primary goal of iterrows() is to provide a way to loop through each row of a DataFrame as a Series object, which allows you to access the row's data by column name.
- **Return Value**: For each row, iterrows() returns a tuple containing:
  - The **index** of the row.
  - A **Series** object representing the data in that row.
- **Usage**: iterrows() is useful for scenarios where vectorized operations (which are typically faster) are not possible or when one needs to perform calculations or logic that depend on multiple columns.

**Syntax**

The basic syntax for iterrows() is:

for index, row in df.iterrows():

\# Access row data

**Detailed Example**

Let's go through an example to understand how iterrows() works:

**Sample DataFrame**

Assume we have a DataFrame containing information about employees:

| **Index** | **Name** | **Age** | **Department** | **Salary** |
| --- | --- | --- | --- | --- |
| 0   | Alice | 30  | HR  | 70000 |
| 1   | Bob | 25  | IT  | 80000 |
| 2   | Charlie | 35  | Finance | 90000 |

import pandas as pd

\# Create a sample DataFrame

data = {

'Name': \['Alice', 'Bob', 'Charlie'\],

'Age': \[30, 25, 35\],

'Department': \['HR', 'IT', 'Finance'\],

'Salary': \[70000, 80000, 90000\]

}

df = pd.DataFrame(data)

**Iterating Over the DataFrame**

Now, let’s use iterrows() to iterate through each row in the DataFrame and print information about the employees.

for index, row in df.iterrows():

print(f"Index: {index}, Name: {row\['Name'\]}, Age: {row\['Age'\]}, Department: {row\['Department'\]}, Salary: {row\['Salary'\]}")

**Expected Output**

The output of this loop would be:

Index: 0, Name: Alice, Age: 30, Department: HR, Salary: 70000

Index: 1, Name: Bob, Age: 25, Department: IT, Salary: 80000

Index: 2, Name: Charlie, Age: 35, Department: Finance, Salary: 90000

**Modifying Data Within the Loop**

You might also want to perform calculations or modify the data while iterating over it. However, remember that modifying the DataFrame within an iterrows() loop is not the most efficient approach. Here's an example of calculating bonuses based on salary:

\# Create a new column for bonuses calculated in the loop

bonuses = \[\]

for index, row in df.iterrows():

if row\['Salary'\] < 80000:

bonuses.append(row\['Salary'\] \* 0.10) # 10% bonus for salary < 80000

else:

bonuses.append(row\['Salary'\] \* 0.05) # 5% bonus for salary >= 80000

df\['Bonus'\] = bonuses

**Resulting DataFrame**

After the loop, the DataFrame would look like this:

| **Index** | **Name** | **Age** | **Department** | **Salary** | **Bonus** |
| --- | --- | --- | --- | --- | --- |
| 0   | Alice | 30  | HR  | 70000 | 7000.0 |
| 1   | Bob | 25  | IT  | 80000 | 4000.0 |
| 2   | Charlie | 35  | Finance | 90000 | 4500.0 |

**Efficiency Considerations**

While iterrows() is easy to use, it is **not the most efficient method** for large DataFrames. This is because it converts rows into a Series when iterating, which is slower than direct vectorized operations.

For better performance, consider vectorized operations, apply(), or list comprehensions wherever possible. Here’s how you could achieve the bonus calculation using a vectorized approach instead:

df\['Bonus'\] = df\['Salary'\].apply(lambda x: x \* 0.10 if x < 80000 else x \* 0.05)

**More Detailed Examples**

1. **Filtering and Summarizing Data**:  
    You can use iterrows() to filter data based on certain conditions.
2. for index, row in df.iterrows():
3. if row\['Department'\] == 'IT':
4. print(f"{row\['Name'\]} works in IT with a salary of {row\['Salary'\]}.")
5. **Creating a Summary**:  
    Create a summary of employees' ages in each department:
6. age_summary = {}
7. for index, row in df.iterrows():
8. if row\['Department'\] not in age_summary:
9. age_summary\[row\['Department'\]\] = \[\]
10. age_summary\[row\['Department'\]\].append(row\['Age'\])
11. for dept, ages in age_summary.items():
12. print(f"Average age in {dept}: {sum(ages) / len(ages):.2f}")
13. **Combining Data from Two DataFrames**:  
    If you have two DataFrames and want to combine information based on certain conditions using iterrows, you can do it similarly.

**Summary**

- The iterrows() function provides a straightforward method to access DataFrame rows one at a time for more granular operations.
- It returns each row as a Series object indexed by column names, making it easy to perform operations based on the values of specific columns.
- While useful for smaller DataFrames or less complex operations, iterrows() is less efficient for larger DataFrames compared to vectorized operations.
- For performance reasons, consider using it judiciously and explore alternative methods for larger datasets.
