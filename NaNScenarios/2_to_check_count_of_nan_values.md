To count the number of NaN (Not a Number) values in a specific column of a Pandas DataFrame (in this case, Switch_Number from the switch_df DataFrame), you can use the isna() method along with the sum() method. Here’s how you can do it:

import pandas as pd

\# Assuming you already have your DataFrame \`switch_df\`

nan_count = switch_df\['Switch_Number'\].isna().sum()

print(f'Number of NaN values in Switch_Number: {nan_count}')

**Explanation:**

- switch_df\['Switch_Number'\]: This selects the column named Switch_Number from the DataFrame.
- .isna(): This method returns a boolean Series indicating where the values are NaN (True for NaN and False for non-NaN).
- .sum(): This adds up the True values in the boolean Series, effectively counting the number of NaN values since True is treated as 1 and False as 0.

As a result, nan_count will hold the total number of NaN values in the Switch_Number column. You can then print or use this count as needed.
