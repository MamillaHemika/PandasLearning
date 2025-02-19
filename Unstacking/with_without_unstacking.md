Unstacking is a powerful feature in Pandas that allows you to reshape data from long to wide format. Here are a few more examples to illustrate how unstacking works:

**Example 1: Simple Grouping**

Let's create a sample DataFrame that represents some sales data for different products sold in different regions.

**Sample DataFrame:**

import pandas as pd

data = {

'Region': \['North', 'North', 'South', 'South', 'East', 'East'\],

'Product': \['A', 'B', 'A', 'B', 'A', 'B'\],

'Sales': \[150, 200, 100, 250, 75, 100\]

}

df = pd.DataFrame(data)

print(df)

**Output:**

Region Product Sales

0 North A 150

1 North B 200

2 South A 100

3 South B 250

4 East A 75

5 East B 100

**Group by Region and Product and Size**

We will group by Region and Product, sum the sales, and then unstack:

sales_analysis = df.groupby(\['Region', 'Product'\]).sum().unstack(fill_value=0)

print(sales_analysis)

**Output:**

Sales

Product A B

Region

East 75 100

North 150 200

South 100 250

**Explanation:**

- The index is Region, and the columns are the Products that represent the sales totals.
- For example, in the North region, Sales for product A is 150, and for product B it is 200.

**Example 2: Using MultiIndex**

Let’s create a more complex DataFrame with temperature readings for different cities across different months.

**Sample DataFrame:**

data = {

'City': \['New York', 'New York', 'New York', 'Los Angeles', 'Los Angeles', 'Chicago', 'Chicago'\],

'Month': \['January', 'February', 'March', 'January', 'February', 'January', 'February'\],

'Temperature': \[30, 32, 50, 58, 60, 28, 30\]

}

df_temp = pd.DataFrame(data)

print(df_temp)

**Output:**

City Month Temperature

0 New York January 30

1 New York February 32

2 New York March 50

3 Los Angeles January 58

4 Los Angeles February 60

5 Chicago January 28

6 Chicago February 30

**Group by City and Month**

Now we will group by City and Month, and unstack the data:

temperature_analysis = df_temp.groupby(\['City', 'Month'\]).sum().unstack(fill_value=0)

print(temperature_analysis)

**Output:**

Temperature

Month January February March

City

Chicago 28 30 0

Los Angeles 58 60 0

New York 30 32 50

**Explanation:**

- In the resulting table, the rows represent City, and the columns represent Month, with the values being the Temperature.
- For New York in January, the temperature is 30, while in February, it is 32, and in March, it is 50.

**Example 3: Real Aggregation with More Types**

Let's consider a hypothetical dataset of athletes’ scores at different sports events.

**Sample DataFrame:**

data = {

'Athlete': \['Alice', 'Bob', 'Alice', 'Bob', 'Alice', 'Bob'\],

'Event': \['100m', '100m', '200m', '200m', 'Long Jump', 'Long Jump'\],

'Score': \[11.5, 10.3, 23.1, 22.8, 6.5, 6.7\],

}

df_scores = pd.DataFrame(data)

print(df_scores)

**Output:**

Athlete Event Score

0 Alice 100m 11.5

1 Bob 100m 10.3

2 Alice 200m 23.1

3 Bob 200m 22.8

4 Alice Long Jump 6.5

5 Bob Long Jump 6.7

**Group by Athlete and Event**

Now let's group by Athlete and Event, and unstack to see their scores:

score_analysis = df_scores.groupby(\['Athlete', 'Event'\]).sum().unstack(fill_value=0)

print(score_analysis)

**Output:**

Event 100m 200m Long Jump

Athlete

Alice 11.5 23.1 6.5

Bob 10.3 22.8 6.7

**Explanation:**

- This output gives a clear visual mapping of scores attained by each athlete in different events.
- For example, Alice scored 11.5 in the 100m event and 23.1 in the 200m event.

**Summary**

- **Unstacking** converts a multi-level index (MultiIndex) or a grouped Series into a DataFrame, changing rows into columns.
- It can help in reshaping the data for better analysis and visualization.
- It is particularly useful for aggregating and summarizing categorical data in a more user-friendly format.

If you have any other specific scenarios or types of data you want to explore, feel free to let me know!

Below are the same examples as before, but without using the .unstack() method. This will help illustrate how the data looks in a more traditional, long format after aggregation without reshaping it into a wide format.

**Example 1: Simple Grouping Without Unstacking**

**Sample DataFrame:**

import pandas as pd

data = {

'Region': \['North', 'North', 'South', 'South', 'East', 'East'\],

'Product': \['A', 'B', 'A', 'B', 'A', 'B'\],

'Sales': \[150, 200, 100, 250, 75, 100\]

}

df = pd.DataFrame(data)

print(df)

**Output:**

Region Product Sales

0 North A 150

1 North B 200

2 South A 100

3 South B 250

4 East A 75

5 East B 100

**Group by Region and Product Without Unstacking**

Now, we'll group by Region and Product, and aggregate (sum) sales, without unstacking:

sales_analysis = df.groupby(\['Region', 'Product'\]).sum()

print(sales_analysis)

**Output:**

Sales

Region Product

East A 75

B 100

North A 150

B 200

South A 100

B 250

**Explanation:**

- The output remains in a long format, showing the Region and Product as a multi-level index.
- Sales are aggregated but the data is not reshaped. Each row represents a unique combination of Region and Product.

**Example 2: Using MultiIndex Without Unstacking**

**Sample DataFrame:**

data = {

'City': \['New York', 'New York', 'New York', 'Los Angeles', 'Los Angeles', 'Chicago', 'Chicago'\],

'Month': \['January', 'February', 'March', 'January', 'February', 'January', 'February'\],

'Temperature': \[30, 32, 50, 58, 60, 28, 30\]

}

df_temp = pd.DataFrame(data)

print(df_temp)

**Output:**

City Month Temperature

0 New York January 30

1 New York February 32

2 New York March 50

3 Los Angeles January 58

4 Los Angeles February 60

5 Chicago January 28

6 Chicago February 30

**Group by City and Month Without Unstacking**

Now let's group by City and Month, and aggregate (sum) temperatures without unstacking:

temperature_analysis = df_temp.groupby(\['City', 'Month'\]).sum()

print(temperature_analysis)

**Output:**

Temperature

City Month

Chicago January 28

February 30

Los Angeles January 58

February 60

New York January 30

February 32

March 50

**Explanation:**

- The output is again in a long format with a multi-level index showing City and Month.
- It displays the temperature data aggregated by each unique combination of city and month without reshaping.

**Example 3: Athlete Scores Without Unstacking**

**Sample DataFrame:**

data = {

'Athlete': \['Alice', 'Bob', 'Alice', 'Bob', 'Alice', 'Bob'\],

'Event': \['100m', '100m', '200m', '200m', 'Long Jump', 'Long Jump'\],

'Score': \[11.5, 10.3, 23.1, 22.8, 6.5, 6.7\],

}

df_scores = pd.DataFrame(data)

print(df_scores)

**Output:**

Athlete Event Score

0 Alice 100m 11.5

1 Bob 100m 10.3

2 Alice 200m 23.1

3 Bob 200m 22.8

4 Alice Long Jump 6.5

5 Bob Long Jump 6.7

**Group by Athlete and Event Without Unstacking**

Now let's group by Athlete and Event, and aggregate (sum) scores without unstacking:

score_analysis = df_scores.groupby(\['Athlete', 'Event'\]).sum()

print(score_analysis)

**Output:**

Score

Athlete Event

Alice 100m 11.5

200m 23.1

Long Jump 6.5

Bob 100m 10.3

200m 22.8

Long Jump 6.7

**Explanation:**

- The resulting output is again in long format with a multi-level index showing Athlete and Event.
- It provides total scores per athlete for each event, but the data is not reshaped into a wide format.

**Summary**

In each of the examples above, we demonstrated how to **group and aggregate data** using .groupby() without transforming the data with .unstack(). The main difference is that:

- **Using unstack()** reshapes the DataFrame so that one or more levels of the index (in this case, the second level of the multi-index) become columns, resulting in a wider format that can make comparisons easier visually.
- **Without unstack()**, the output retains a longer format where each unique combination of the grouped columns (e.g., Region, City, Athlete) is presented individually, which is useful for certain analyses but may be less intuitive for quick visual comparisons.
