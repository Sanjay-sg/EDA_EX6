## Build Cartographic Visualization for Multiple Datasets Involving Various Countries of the World; States and Districts in India

### AIM:
~~~
Build Cartographic Visualization for Multiple Datasets Involving Various Countries of the World; States and Districts in India
~~~
### PROGRAM:
~~~
# Step 1: Import required libraries
import pandas as pd
import folium
# Step 2: Load the world GeoJSON (for country boundaries)
geojson_url = "https://raw.githubusercontent.com/python-visualization/folium/master/examples/data/world-countries.json"

# Step 3: Load the GDP data for countries
gdp_url = "https://raw.githubusercontent.com/plotly/datasets/master/2014_world_gdp_with_codes.csv"
gdp_df = pd.read_csv(gdp_url)

# Step 4: Create a base map
world_map = folium.Map(location=[20, 0], zoom_start=2)

# Step 5: Add choropleth layer
folium.Choropleth(
    geo_data=geojson_url,
    name='choropleth',
    data=gdp_df,
    columns=['CODE', 'GDP (BILLIONS)'],
    key_on='feature.id',
    fill_color='YlGnBu',
    fill_opacity=0.7,
    line_opacity=0.2,
    legend_name='GDP in Billions (USD)'
).add_to(world_map)

# Step 6: Add layer control
folium.LayerControl().add_to(world_map)

# Step 7: Save map to HTML
world_map.save("world_gdp_map.html")
print("Cartographic GDP map saved as 'world_gdp_map.html'. Open it in a browser to view the interactive map.")
~~~
