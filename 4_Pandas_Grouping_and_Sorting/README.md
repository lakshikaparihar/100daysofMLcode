# Grouping and Sorting

<br>

## 👉 `groupby` function

<br>

   ```
   reviews.groupby("points").points.count()
   ```

<br>

`groupby()` created a group of reviewswhich     allotted the same point valuesto the given     wines. Then, for eachof these groups, we     grabbed the`points` column and counted how     manytimes it appeared. `value_counts()` is   just a shortcut to this `groupby()`     operation.

<br>

### ⁉️ How to get the cheapest wine in each point value category
<br>

```
reviews.groupby("points").price.min()
```

<br>

### ⁉️ price of First wine reviewed from each winery
<br>

```
reviews.groupby("winery").apply(lambda df:df.price.iloc[0])
```
<br>

### ⁉️ How to pick out best wine by country and province
<br>

```
reviews.groupby(["country","province"]).apply(lambda df:df.loc[df.points.idxmax()])
```

<br>

### ⁉️ Genereating a simple statistical summary of the dataset
<br>

```
reviews.groupby("country").price.agg([len,min,max])
```

<br>

### ⁉️ How to Convert multi-index back to regular index
<br>

```
countries_reviewed.reset_index()
```


<br>

## 👉 Sorting

<br>

1. &nbsp; Sort by value : `sort_values()`
    
    * 
       ```
       countries_reviewed.sort_values(by='len')
       ```

    * By default the sorting is done in ascending order , for descending sorting we can do the following

      ```
      countries_reviewed.sort_values(by='len', ascending=False)
      ```

    * for sorting more than one column at a time
       ```
       countries_reviewed.sort_values(by=['country', 'len'])
       ```

2. &nbsp; Sort by index : `sort_index()`

     * 
        ```
        countries_reviewed.sort_index()
        ```

<br>
Check out the [notebook](https://github.com/lakshikaparihar/100daysofMLcode/blob/4389916b324c3f250d7e07dedcca07be00682aaf/4_Pandas_Grouping_and_Sorting/Exercise/exercise.ipynb) for the example
