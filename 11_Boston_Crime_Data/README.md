# Interactive Map

Several arguments customize the appearance of the map:

* `location` sets the initial center of the map. We use the latitude (42.32° N) and longitude (-71.0589° E) of the city of Boston.
* `tiles` changes the styling of the map; in this case, we choose the OpenStreetMap style. List of titles are [here](https://github.com/python-visualization/folium/tree/master/folium/templates/tiles)
* `zoom_start` sets the initial level of zoom of the map, where higher values zoom in closer to the map.

<br>


# Bubble Map

Note that `folium.Circle()` takes several arguments:

* `location` is a list containing the center of the circle, in latitude and longitude.
* `radius` sets the radius of the circle.
Note that in a traditional bubble map, the radius of each circle is allowed to vary. We can implement this by defining a function similar to the color_producer() function that is used to vary the color of each circle.
color sets the color of each circle.
* The `color_producer()` function is used to visualize the effect of the hour on robbery location.

<br>

# HeatMaps

As you can see in the code cell above, folium.plugins.HeatMap() takes a couple of arguments:

* `data` is a DataFrame containing the locations that we'd like to plot.
* `radius` controls the smoothness of the heatmap. Higher values make the heatmap look smoother (i.e., with fewer gaps).

<br>

