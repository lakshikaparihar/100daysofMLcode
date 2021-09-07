# Getting Started with Pandas

## 👉 Importing pandas

```
 import pandas as pd
```
<br>

## 👉 Creating Data
<br>
<font size="3"> There are two core objects in pandas : Dataframe,Series</font> 
<br>
<br>

### 🤔 How to create a DataFrame ?

Dataframe is a table which contains an array of individual entries, each of which has a certain value. Each entry corresponds to a row and a column.
<br>

```
pd.DataFrame({'Person' :["Derek","Meredith"],'Dialogue':["Its a beautiful day to save lives","She is my person"]})
```
**Output :**
| | Person  | Dialogue  |
| :---:   | :-: | :-: |
| 0 | Derek | Its a beautiful day to save lives |
| 1 | Meredith | She is my person |

<br>

### 🤔 How to change the index ?
```
pd.DataFrame({'Person' :["Derek","Meredith"],'Dialogue':["Its a beautiful day to save lives","She is my person"]},index=["Neuro","General"])
```

**Output :**
| | Person  | Dialogue  |
| :---:   | :-: | :-: |
| Neuro | Derek | Its a beautiful day to save lives |
| General | Meredith | She is my person |

### 🤔 How to create a Series ?

A series is a sequence of data values. If a dataframe is a table then series is a list.

```
pd.Series([1,2,3,4,5])
```

**Output :**<br>
0  1 <br>
1  2 <br>
2  3 <br>
3  4 <br>
4  5 <br>
dtype: int64

### 🤔 How to change the index ?
Series is a single column of a DataFrame. So we can assign coulmn values to the series the same way as before but a series does not have a column name, it only has one overall name

```
pd.Series([1,2,3,4,5],index=['A','B','C','D','E'],name="Alphabet")
```

**Output :**<br>
A  1 <br>
B  2 <br>
C  3 <br>
D  4 <br>
E  5 <br>
Name: Alphabet dtype: int64

## 👉 Reading data files

Data can be stored in any format but most basic of these is the CSV file. It  is a table of values separated by commas. Hence the name `Comma-Separated Values`, or `CSV`

### 🤔 How to Read data from a CSV file ?

```
df = pd.read_csv(file_name)
```

### 🤔 How to check the no. of rows or columns our data has ?

```
df.shape
```

### 🤔 As there can be millions record in our data so how can we read only few rows?

```
df.head()
```

### 🤔 How to use one of the column from the data as index?
```
df = pd.read_csv(file_name,index_col=0)
```

## 👉 Saving dataFrame to a CSV file

```
df.to_csv(file_name)
```