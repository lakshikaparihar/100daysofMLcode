# Indexing , Slicing , Assigning



 Dataframe used is `reviews`


|| Unnamed: 0 |	country|description	|designation|points|price|province|	region_1|region_2|variety |winery|
| :---: |:--:      | :-:    | :-:             |:---:      |:---: |:---:| :-:    | :-:     |:---:   | :-:     | :-: |
|0 |0  |US    |  This tremendous 100% varietal wine hails from ... |Martha's Vineyard | 96 |235.0| California| Napa Valley |Napa |Cabernet |Sauvignon Heitz|
|1 |	1 |Spain |	Ripe aromas of fig, blackberry and cassis are ...|	Carodorum Selección Especial Reserva |	96|	110.0| 	Northern Spain|	Toro	|NaN	|Tinta de Toro|	Bodega Carmen Rodríguez|
|2 |	2 |US	 |Mac Watson honors the memory of a wine once ma...   |Special Selected Late Harvest|	96|	90.0|	California| Knights Valley|	Sonoma|	Sauvignon Blanc	|Macauley|
|3 |	3 |US	 |This spent 20 months in 30% new French oak, an...	  |Reserve|	96|	65.0|	Oregon|	Willamette Valley|	Willamette Valley|	Pinot Noir|	Ponzi|
|4 |	4 |France|	This is the top wine from La Bégude, named aft...|	La Brûlade|	95|	66.0|	Provence|	Bandol|	NaN	|Provence red blend	|Domaine de la Bégud|

<br>

## 👉 Accessing Columns of Dataframe

There are two ways by which we can access its column and both returns the same output: :

1. Using dot(.)
   ```
   reviews.country
   ```

2. Using index([])
   ```
   reviews['country']
   ```

**Output :**

0             US <br>
1          Spain <br>
           ...   <br>
150928    France <br>
150929     Italy <br>
Name: country, Length: 150930, dtype: object

## 👉 Accessing Specific value of a Dataframe
<br>

```
reviews['country'][1]
```
**Output :**

'spain'

## 👉 Selecting data based on its numerical position `iloc` [row-first , column-second]


* 1st row of every column

  ```
  reviews.iloc[1]
  ```
* every row of 1st column

  ```
  reviews.iloc[:,1]
  ```

* First 3 rows of 0th column

  ```
  reviews.iloc[[0, 1, 2], 0]
  ```
* Last 5 rows

  ```
  reviews.iloc[-5:]
  ```


## 👉 Selecting data based on its label `loc` [row-first , column-second]
<br>

* 0th row of country column
  ```
  reviews.loc[0, 'country']
  ```

* every row of specified columns
  ```
  reviews.loc[:, ['country','description','designation']]
  ```

### ⁉️ What's the difference between `iloc` and `loc`?

loc includes both first and last index of range whereas iloc includes only the first and excludes the last index

Example :

* loc -> will return 3 rows for the following

   ```
   reviews.loc[0:2]
   ```

* iloc -> will return 2 rows for the same

   ```
   reviews.iloc[0:2]
   ```

## 👉 Manuplating the index

Now the first column of our dataframe will be the index

```
reviews.set_index("Unnamed: 0")
```

## 👉 Conditional selection

* Suppose that we're interested specifically in better-than-average wines produced in Italy.

    1. check if the wine is italian or not , it will return a series of true or false

       ```
       reviews.country == "Italy"
       ```
    2. We can use it to get the relevant data , so choose only those rows whose country is "Italy"

       ```
       reviews.loc[reviews.country=="Italy"]
       ```

    3. Last thing it should be above average so we will put another condition

       ```
       reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]
       ```

* Suppose we'll buy any wine that's made in Italy or which is rated above average.

  ```
  reviews.loc[(reviews.country == 'Italy') | (reviews.points >= 90)]
  ```

## Built-in conditional selectors
<br>

* `isin` : choose wine only from France and Italy

   ```
   reviews.loc[reviews.country.isin(['France','Italy'])]
   ```

* `isnull` and `notnull` : Filter out wines which does not have a price tag

   ```
   reviews.loc[reviews.price.notnull()]
   ```

## 👉 Assigning Data

* Assigning a constant value
   
    ```
    reviews['points'] = 100
    ```

* Assigning iterable of Values

    ```
    reviews['points'] = random.randint(0,200)
    ```
    
<br>

Check out the [notebook](https://github.com/lakshikaparihar/100daysofMLcode/blob/a0149ed4937df81fb85a1c6121da3c4f15f2253a/2_Pandas_Data_Manipulation/Exercise/Exercise.ipynb) for the example
