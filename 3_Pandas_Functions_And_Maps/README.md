# Functions and Maps

Dataframe used is `reviews`


|| Unnamed: 0 |	country|description	|designation|points|price|province|	region_1|region_2|variety |winery|
| :---: |:--:      | :-:    | :-:             |:---:      |:---: |:---:| :-:    | :-:     |:---:   | :-:     | :-: |
|0 |0  |US    |  This tremendous 100% varietal wine hails from ... |Martha's Vineyard | 96 |235.0| California| Napa Valley |Napa |Cabernet |Sauvignon Heitz|
|1 |	1 |Spain |	Ripe aromas of fig, blackberry and cassis are ...|	Carodorum Selección Especial Reserva |	96|	110.0| 	Northern Spain|	Toro	|NaN	|Tinta de Toro|	Bodega Carmen Rodríguez|
|2 |	2 |US	 |Mac Watson honors the memory of a wine once ma...   |Special Selected Late Harvest|	96|	90.0|	California| Knights Valley|	Sonoma|	Sauvignon Blanc	|Macauley|
|3 |	3 |US	 |This spent 20 months in 30% new French oak, an...	  |Reserve|	96|	65.0|	Oregon|	Willamette Valley|	Willamette Valley|	Pinot Noir|	Ponzi|
|4 |	4 |France|	This is the top wine from La Bégude, named aft...|	La Brûlade|	95|	66.0|	Provence|	Bandol|	NaN	|Provence red blend	|Domaine de la Bégud|

<br>

## 👉 Summary function
<br>


### ⁉️ How to get the summary of all the statistics
<br>

```
reviews.points.describe()
```

---     
**Output :**

count &nbsp;&nbsp;    150930.000000 <br>
mean &nbsp;&nbsp;        87.888418 <br>
std  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;         3.222392 <br>
min &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;      80.000000 <br>
25%    &nbsp;&nbsp;&nbsp;&nbsp;      86.000000 <br>
50%   &nbsp;&nbsp;&nbsp;&nbsp;       88.000000 <br>
75%   &nbsp;&nbsp;&nbsp;&nbsp;       90.000000 <br>
max   &nbsp;&nbsp;&nbsp;&nbsp;      100.000000 <br>
Name: points, dtype: float64

---

<font size="3"> The summary function output changes based on the data type of the input</font> 

<br>


```
reviews.region_1.describe()
```
<br>

---
**Output :**
count   &nbsp; &nbsp;        125870 <br>
unique   &nbsp;         1236 <br>
top   &nbsp; &nbsp; &nbsp; &nbsp;     Napa Valley <br>
freq    &nbsp; &nbsp; &nbsp; &nbsp;          6209 <br>
Name: region_1,&nbsp;  dtype: object

---

<br>

### ⁉️ How to get the mean of a column

<br>

```
reviews.points.mean()
```
**Output :** 87.8884184721394

<br>

### ⁉️ How to get all the unique values of a column

<br>

```
reviews.region_1.unique()
```

<br>

### ⁉️ How to get the occurence of every value of a column

<br>

```
reviews.region_1.value_counts()
```

<br>

---
Napa Valley &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6209 <br>
Mendoza&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3586 <br>
Russian River Valley&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3571 <br>
                               ...  <br>
Coteaux du Lyonnais&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 <br>
Niagara Escarpment&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 <br>
Alpine Valleys&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 <br>
Michigan&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 <br>
Name: region_1, Length: 1236, dtype: int64

---

<br>

## 👉 Maps
<br>


A map is a term, borrowed from mathematics, for a function that takes one set of values and "maps" them to another set of values.

<br>


```
review_points_mean = reviews.points.mean()
reviews.points.map(lambda p: p - review_points_mean)
```


The function you pass to `map()` should expect a single value from the Series (a point value, in the above example), and return a transformed version of that value. `map()` returns a new Series where all the values have been transformed by your function.

<br>
Above we are mapping all the value of points with (p - p's mean) and it will return a series of updated value but it won't still make any difference in your dataframe because we didn't change anything in our dataframe
</font>

<br>
<br>


`apply()` is the equivalent method if we want to transform a whole DataFrame by calling a custom method on each row.

```
def remean_points(row):
    row.points = row.points - review_points_mean
    return row

reviews.apply(remean_points, axis='columns')
```

<br>

There is another way in which Pandas looks at the expression and figures out that we must mean to subtract that mean value from every value in the dataset.

<br>

```
review_points_mean = reviews.points.mean()
reviews.points - review_points_mean
```
Pandas will also understand what to do if we perform these operations between Series of equal length.

```
reviews.country + " - " + reviews.region_1
```
<br>

### ⁉️ How to get the value a column according to the maximum value of another column (`idxmax`)

<br>

```
bargain_idx = (reviews.points / reviews.price).idxmax()
bargain_wine = reviews.loc[bargain_idx, 'variety']
bargain_wine
```

idxmax returns the index of the maximum value of the column