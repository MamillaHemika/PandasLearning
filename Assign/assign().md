The assign() function in pandas is used to add new columns to a DataFrame or to modify existing columns. It returns a new DataFrame with the changes without modifying the original DataFrame (since DataFrames are immutable). This function is useful for creating new calculated columns or modifying columns in a readable way.

**Syntax**

DataFrame.assign(\*\*kwargs)

- **Parameters**:
  - You can pass keyword arguments (\*\*kwargs), where the keys are the names of the new or existing columns and the values are the data or expressions used to compute those values.
- **Return Value**: A new DataFrame with the added or modified columns.

**Characteristics of assign()**

- **Non-Invasive**: The original DataFrame remains unchanged; assign() creates a copy.
- **Chaining**: You can chain it with other DataFrame methods for cleaner code.
- **Flexible**: You can pass any valid pandas expression to compute the value of the new column.

**Examples of assign()**

**Initial Setup**

Let’s create a sample DataFrame for demonstrating the assign() function:

import pandas as pd

\# Sample DataFrame

data = {

'Name': \['Alice', 'Bob', 'Charlie'\],

'Age': \[24, 30, 22\],

'Salary': \[70000, 80000, 60000\]

}

df = pd.DataFrame(data)

print("Original DataFrame:")

print(df)

**Example 1: Basic Usage of assign()**

You can use assign() to create a new column based on existing columns.

\# Adding a new column 'Bonus' that is 10% of Salary

df_with_bonus = df.assign(Bonus=lambda x: x\['Salary'\] \* 0.10)

print("\\nDataFrame with Bonus:")

print(df_with_bonus)

**Output**

Original DataFrame:

Name Age Salary

0 Alice 24 70000

1 Bob 30 80000

2 Charlie 22 60000

DataFrame with Bonus:

Name Age Salary Bonus

0 Alice 24 70000 7000.0

1 Bob 30 80000 8000.0

2 Charlie 22 60000 6000.0

In this example, a new column named Bonus is added, which calculates 10% of each employee's salary.

**Example 2: Modifying an Existing Column**

You can also use assign() to modify an existing column. For instance, let's convert the Salary into a higher format, say thousands.

\# Modifying Salary to represent thousands

df_mod_salary = df.assign(Salary=lambda x: x\['Salary'\] / 1000)

print("\\nDataFrame with Modified Salary:")

print(df_mod_salary)

**Output**

DataFrame with Modified Salary:

Name Age Salary

0 Alice 24 70.0

1 Bob 30 80.0

2 Charlie 22 60.0

**Example 3: Adding Multiple Columns**

You can add multiple new columns in one go by passing additional keyword arguments.

\# Add multiple new columns: 'Years to Retirement' and 'Hourly Wage'

df_multiple = df.assign(

Years_to_Retirement=lambda x: 65 - x\['Age'\],

Hourly_Wage=lambda x: x\['Salary'\] / 2080 # Assuming 2080 working hours in a year

)

print("\\nDataFrame with Multiple New Columns:")

print(df_multiple)

**Output**

DataFrame with Multiple New Columns:

Name Age Salary Years_to_Retirement Hourly_Wage

0 Alice 24 70000 41.0 33.65

1 Bob 30 80000 35.0 38.46

2 Charlie 22 60000 43.0 28.85

**Example 4: Chaining with Other DataFrame Methods**

The assign() function can be easily chained with other DataFrame operations for improved readability.

\# Chaining operations: Filter, Assign and Sort by Salary

result = (df

.assign(Bonus=lambda x: x\['Salary'\] \* 0.10)

.query('Bonus > 7000')

.sort_values(by='Salary', ascending=False))

print("\\nChained Operations Result:")

print(result)

**Output**

Chained Operations Result:

Name Age Salary Bonus

1 Bob 30 80000 8000.0

**Example 5: Using Values from Other Columns**

You can also compute a new column based on multiple existing columns.

\# Create a new column 'Total Compensation' based on Salary and Bonus

df_total_comp = df.assign(Total_Compensation=lambda x: x\['Salary'\] + (x\['Salary'\] \* 0.10))

print("\\nDataFrame with Total Compensation:")

print(df_total_comp)

**Output**

DataFrame with Total Compensation:

Name Age Salary Total_Compensation

0 Alice 24 70000 77000.0

1 Bob 30 80000 88000.0

2 Charlie 22 60000 66000.0

**Summary**

- The assign() function is a powerful method in pandas for adding and modifying columns within a DataFrame.
- It allows for clean, readable, and chained DataFrame operations.
- The ability to use lambda functions makes assign() extremely versatile, allowing for dynamic calculations based on existing data.
- Keep in mind that assign() does not modify the original DataFrame but rather returns a new one with the modifications.

**Practical Applications**

- **Data Transformation**: Creating and transforming columns based on business logic and calculations without altering the original dataset.
- **Data Cleaning**: Making adjustments and cleaning data using calculations before conducting analysis or modeling.
