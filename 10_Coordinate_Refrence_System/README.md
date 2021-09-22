As we know World is actually a 3D globe , so it render it as a flat surface we use a method called `Map Projection`.


Map Projection aren't 100% accurate as projection distorts the surface of the earth is some way , while retaining some useful property .For instance

* the `equal-area projections` preserve area. This is a good choice, if you'd like to calculate the area of a country or city, for example.

* the `equidistant projections` preserve distance. This would be a good choice for calculating flight distance.

### ⁉️ How to check the Espg(European Petroleum Survey Group) code 

<br>

```python
regions.crs
```


Coordinate reference systems are referenced by European Petroleum Survey Group (EPSG) codes.

This GeoDataFrame uses EPSG 32630, which is more commonly called the "Mercator" projection. This projection preserves angles (making it useful for sea navigation) and slightly distorts area.

However, when creating a GeoDataFrame from a CSV file, we have to set the CRS. EPSG 4326 corresponds to coordinates in latitude and longitude.

<br>

### ⁉️ How to create a GeoDataFrame from a CSV file


* We begin by creating a DataFrame containing columns with latitude and longitude coordinates.
  ```python
  df = pd.read_csv(csv_file_path)
  ```

* To convert it to a GeoDataFrame, we use gpd.GeoDataFrame().
  ```python
  geo_df = gpd.GeoDataFrame(df, geometry=gpd.points_from_xy(df.Longitude, df.Latitude))
  ```

* The gpd.points_from_xy() function creates Point objects from the latitude and longitude columns.

### ⁉️ How to set CRS

```python
df.crs = {'init': 'epsg:4326'}
```

## 👉 Re-Projecting

<br>
When plotting multiple GeoDataFrames, it's important that they all use the same CRS. In the code cell below, we change the CRS of the facilities GeoDataFrame to match the CRS of regions before plotting it.
<br>
<br>

```python
df.to_crs(epsg=32630)
```

### ⁉️ In case the EPSG code is not available in GeoPandas

```python
regions.to_crs("+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs")
```
<br>

## 👉 Attributes of Geometric Object

* a `Point` for the epicenter of an earthquake,
* a `LineString` for a street, or
* a `Polygon` to show country boundaries.

```python
# point coordinates
df.geometry.x
# linestring coordinates
df.geometry.length
# Ploygon coordinates
df.geometry.area
```

