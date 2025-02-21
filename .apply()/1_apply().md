We will use the same DataFrame as before:

import pandas as pd

\# Create a simple DataFrame

data = {

'EIN': \['12-3456789', '98-7654321', '22-3334445'\],

'FTE': \[10, 20, 15\]

}

df = pd.DataFrame(data)

The DataFrame df looks like this:

| **Index** | **EIN** | **FTE** |
| --- | --- | --- |
| 0   | 12-3456789 | 10  |
| 1   | 98-7654321 | 20  |
| 2   | 22-3334445 | 15  |

**Using apply()**

The apply() method can be used to apply a function along the axis of the DataFrame. You can use it to process rows or columns.

**Example: Using apply() to print values**

To replicate the previous example using apply(), we can define a simple function to print the EIN and FTE:

def print_row(row):

print(f"EIN: {row\['EIN'\]}, FTE: {row\['FTE'\]}")

\# Apply the function to each row

df.apply(print_row, axis=1)

**Dry Run for apply()**

Here’s what happens during the execution of this code:

1. **First Application (Row 0)**:
    - row is the Series representing the first row:
    - EIN 12-3456789
    - FTE 10
    - Name: 0, dtype: object
    - Output:
    - EIN: 12-3456789, FTE: 10
2. **Second Application (Row 1)**:
    - row is the Series representing the second row:
    - EIN 98-7654321
    - FTE 20
    - Name: 1, dtype: object
    - Output:
    - EIN: 98-7654321, FTE: 20
3. **Third Application (Row 2)**:
    - row is the Series representing the third row:
    - EIN 22-3334445
    - FTE 15
    - Name: 2, dtype: object
    - Output:

EIN: 22-3334445, FTE: 15
