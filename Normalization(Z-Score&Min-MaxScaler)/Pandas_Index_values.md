# Introduction to Pandas Indexing and Series Attributes

Pandas is one of the most prominent and widely used libraries in the Python ecosystem. It serves as a cornerstone for data manipulation and analysis, making it an indispensable tool for professionals working with structured data, including data scientists, analysts, and researchers. Indexing is a fundamental feature in Pandas that enhances data manipulation, selection, and analysis, making it a powerful tool for working with diverse and structured datasets.

In this module, we are going to explore the world of indexes and values in Pandas, unveiling their significance and utility. Before diving into the topic of indexing, we will first explore the essential attributes of Pandas Series.

Next, we will dedicate some time to mastering the creation of Series objects, a fundamental skill for working effectively with data. In the later sections of the module, we will understand the role of indexes in Pandas Series, understanding their significance and application. With a well-established understanding of indexing fundamentals, we will then explore two distinct types of series indexing:
- Label-based
- Position-based

## Pandas Series

A series is a one-dimensional data structure in Python's Pandas library designed to hold and manipulate labeled homogeneous data, homogeneous here meaning data of the same type. It can be thought of as a labeled array or, in very simplified terms, a column in a table. It consists of both data and an associated index, allowing for effective data retrieval and manipulation.

### Attributes of Pandas Series

Let's get started with the attributes of Pandas Series. The first attribute that we will learn about is the **index**. This attribute returns the labels or positions associated with each element in the series. This attribute allows for efficient data retrieval and alignment, making it a crucial component of the series.

Next, we have **values**. The values attribute of a series returns the data stored in the series. It is returned as a NumPy array or ndarray.

You're probably wondering, wait, aren't NumPy and Pandas two different Python libraries? That is correct. But the short answer is you don't need to import it specifically when working with Pandas, but Pandas depends on and is built upon NumPy. The added advantage of the values attribute is that it allows you to access and manipulate the underlying data with NumPy functions and operations, making it easy to perform numerical computations and transformations.

The next one is **dtype**. The dtype attribute returns the data type of the elements in the series. It is important for understanding the nature of the data in the series, and it is crucial when performing operations and transformations that depend on data types, such as arithmetic operations.

The fourth attribute is **shape**, which returns a tuple representing the shape of the series. This is useful for understanding the size and dimensions of the series when working with data.

The next attribute is **size**. This attribute counts the number of elements in the series, providing a quick way to check the length of the series.

The next attribute of the Pandas Series is **nbytes**. It provides the memory usage in bytes of the data stored in the series, helping to assess the memory footprint of the data. It is valuable for optimizing memory usage and data storage in memory-constrained environments.

The **name** attribute returns the name of the series. It is particularly useful when working with data frames to reference and distinguish series, enhancing data clarity and readability.

The **empty** attribute evaluates whether the series is empty and can be used for conditional checks.

The last attribute that we will explore is **hasnans**, which returns `True` if the series contains any missing (NaN) values. Otherwise, it returns `False`. This attribute is crucial for data quality assessment.

---

By understanding these attributes, you will be better equipped to work with Pandas Series and leverage its powerful features for data manipulation and analysis.
