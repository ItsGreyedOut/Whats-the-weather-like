# Python API Project - What's the Weather Like?

## Background

Whether financial, political, or social -- data's true power lies in its ability to answer questions definitively. So let's take what you've learned about Python requests, APIs, and JSON traversals to answer a fundamental question: "What's the weather like as we approach the equator?"

Now, we know what you may be thinking: _"Duh. It gets hotter..."_

But, if pressed, how would you **prove** it?

![Equator](Images/equatorsign.png)


## Part I - WeatherPy

I created a Python script to visualize the weather of 500+ cities across the world of varying distance from the equator. To accomplish this, I utilized a [simple Python library](https://pypi.python.org/pypi/citipy), the [OpenWeatherMap API](https://openweathermap.org/api), and to create a representative model of weather across world cities.

This visualization will provide a series of scatter plots to showcase the following relationships:

* Temperature (F) vs. Latitude
* Humidity (%) vs. Latitude
* Cloudiness (%) vs. Latitude
* Wind Speed (mph) vs. Latitude

Each plot will profide a breif analysis.

I ran a linear regression on each relationship, separating them into Northern Hemisphere (greater than or equal to 0 degrees latitude) and Southern Hemisphere (less than 0 degrees latitude):

* Northern Hemisphere - Temperature (F) vs. Latitude
* Southern Hemisphere - Temperature (F) vs. Latitude
* Northern Hemisphere - Humidity (%) vs. Latitude
* Southern Hemisphere - Humidity (%) vs. Latitude
* Northern Hemisphere - Cloudiness (%) vs. Latitude
* Southern Hemisphere - Cloudiness (%) vs. Latitude
* Northern Hemisphere - Wind Speed (mph) vs. Latitude
* Southern Hemisphere - Wind Speed (mph) vs. Latitude

After each pair of plots I explain what the linear regression is modeling such as any relationships I notice.

The final notebook contains:

* Randomly select of 500 unique (non-repeat) cities based on latitude and longitude.
* Performed a weather check on each of the cities using a series of successive API calls.
* Includes a print log of each city as it's being processed with the city number and city name.
* A CSV of all retrieved data and a PNG image for each scatter plot.

### Part II - VacationPy

Next I provide the weather data to plan future vacations. I used jupyter-gmaps and the Google Places API to provide this feature.

* I created a heat map to displays the humidity for every city.

  ![heatmap](Images/heatmap.png)

* Narrow down the DataFrame to find your ideal weather condition.

  * A max temperature lower than 80 degrees but higher than 70.

  * Wind speed less than 10 mph.

  * Zero cloudiness.

  * Drop any rows that don't contain all three conditions. You want to be sure the weather is ideal.

  *  I used Google Places API to find the first hotel for each city located within 5000 meters of my coordinates.

* Ploted the hotels on top of the humidity heatmap with each pin containing the **Hotel Name**, **City**, and **Country**.

  ![hotel map](Images/hotel_map.png)


## The Details:

* The city data I generated is based on random coordinates as well as different query times.

* Before I started this project I reviewed the [geographic coordinate system](http://desktop.arcgis.com/en/arcmap/10.3/guide-books/map-projections/about-geographic-coordinate-systems.htm).

* I used OpenWeatherMap API to understand which weather API to utilize in this project.  

* [citipy Python library](https://pypi.python.org/pypi/citipy) was used to provide the nearest cities with geo coordinates. 

* I created a function that will create the charts based on different parameters.

* Each coordinate will trigger a separate call to the Google API. Since I am creating my own criteria to plan my vacation, I reduced the results in my DataFrame to 10 or fewer cities.
