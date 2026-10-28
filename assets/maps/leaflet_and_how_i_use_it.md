Leaflet website:
https://leafletjs.com/

Leaflet examples and tutorials:
https://leafletjs.com/examples.html

The JS in these examples are pretty straightforward and easy to implement in html files. If you download or build a template, it's pretty easy to transfer over point data (in the case of my rainier maps).
Challenges became clear when making maps from polygons, it's a little more complex in terms of formatting than just simple points.

The even bigger challenge came from the temporal aspect we faced with the (veery) migration project... 
To get out of this tricky position, I started by simply exporting the geometry from our gdf (geodata frame). From this, you can convert to a leaflet accepted format (geojson, etc.), there's some good tutorials on this:
I found the easiest way to go about this convversion was through a py package called folium, this way your output was also a leaflet html map. Read more on follium (they use Portland as their intro example, which is where I'm from so I'm a bit biased):
https://folium.readthedocs.io/en/latest/
https://python-visualization.github.io/folium/latest/

I then used this as the foundation to build the nice maps, adding CSS to stylize the borders, adjust for different font types (headings vs sub heading), and to use preferred fonts (my fav is roboto condensed atm).

Once you export you gdf as geojson, just load it:
geojson_data = json.loads(bokeh.geojson)

Initialize:
m = folium.Map(location=[40.0000, -75.0000], zoom_start=12)

And then extract to a leaflet and save!

folium.GeoJson(geojson_data).add_to(m)

m.save("leaflet_map.html")


Regarding the basemaps!
I specifically use Open Street Map since they're awesome and becoming increasingly more universal and broadly accepted. The basemap I use is called "OpenTopoMap" but there's tons others including HOT which is for humanitarian work!
Check some of them out here, this example is specifically through leaflet which made my integration of the basemap in my leaflet super easy:
https://leaflet-extras.github.io/leaflet-providers/preview/
