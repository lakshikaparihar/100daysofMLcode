# Renaming and Combining

## 👉 Renaming

<br>

### ⁉️ How to rename the column
<br>

```
reviews.rename(columns={'points':'score'})
```

<br>

### ⁉️ How to rename the index
<br>

```
reviews.rename(index={0: 'firstEntry', 1: 'secondEntry'})
```

<br>

### ⁉️ How to name the row index and the column index of the dataframe
<br>

```
reviews.rename_axis("wines", axis='rows').rename_axis("fields", axis='columns')
```
<br>


## 👉 Combining

Pandas has three core methods for combining different dataframes. In order of increasing complexity, these are `concat()` , `join()` , and `merge()`.

<br>

* `concat()` is useful when we have different dataframe or series object but having the same fields (columns)

    ```
    canadian_youtube = pd.read_csv("../input/youtube-new/CAvideos.csv")
    british_youtube = pd.read_csv("../input/youtube-new/GBvideos.csv")
    
    pd.concat([canadian_youtube, british_youtube])
    ```

<br>

* `join()` lets you combine different DataFrame objects which have an index in common. 

    ```
    left = canadian_youtube.set_index(['title', 'trending_date'])
    right = british_youtube.set_index(['title', 'trending_date'])
    
    left.join(right, lsuffix='_CAN', rsuffix='_UK')
    ```

