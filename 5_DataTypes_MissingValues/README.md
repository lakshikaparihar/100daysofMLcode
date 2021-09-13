# Data types and Missing Values

## 👉 Datatypes in Pandas

<br>

### ⁉️ How to find the datatype of a column or series
<br>

```
reviews.points.dtype
```

<br>

### ⁉️ How to convert the datatype of the whole column
<br>

```
reviews.points.astype('float64')
```

## 👉 Missing Values

<br>

Entries missing values are given the value `NaN`, short for `"Not a Number"`. For technical reasons these `NaN` values are always of the `float64` dtype.


<br>

### ⁉️ Finding the null value in the dataframe
<br>

```
reviews[pd.isnull(reviews.country)]
```

<br>

### ⁉️ Replacing the null value in the dataframe
<br>

```
reviews.region_2.fillna("Unknown")
```

<br>

### ⁉️ What is `backfill strategy`
<br>

Filling each missing value with the first non-null value that appears sometime after the given record in the database. This is known as the backfill strategy

<br>

### ⁉️ How to replace values in dataframe
<br>

```
reviews.taster_twitter_handle.replace("@kerinokeefe", "@kerino")
```