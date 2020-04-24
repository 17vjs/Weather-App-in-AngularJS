# Weather-App-in-AngularJS
This is a web app for the weather forecast.
1. There is a search for the places using google places API and on click of a `weather report` button, it will display the temperature, humidity, precipitation of that place. This will also display the temperatures of next 7 days.
2. Below this, there is a graph showing the change in the above parameters in the last 5 days.

### Latest technologies used in this [app](./index.html):
* AngularJS
* Chart.js [Link](https://www.chartjs.org/docs/latest/getting-started/)
* Bootstrap
* Google Places API (AutoComplete)
* Open Weather API [current](https://openweathermap.org/current),[one call](https://openweathermap.org/api/one-call-api)

### Requirements
* [Google Maps API Key](https://developers.google.com/maps/documentation/javascript/get-api-key)
* [Open Weather API key](https://openweathermap.org/api)

### Working
1. As you type in, Places are suggested by calling `Google Places API`. Select one of them.
2. Some suggested places doesn't have geometry. Therefore, `getPlace()` function of `google.maps.places.Autocomplete` may or may not return coordinates of that place. Hence we give a call to https://api.openweathermap.org/data/2.5/weather and fetch coordinates from the JSON response.
3. Using the lat and lon, give a call to https://api.openweathermap.org/data/2.5/onecall using `$http`. The `daily` attribute of response gives the weather forecast for next 7 days.
4. Using `ng-repeat` render it in HTML.
5. Calulate timestamp of 5 days ago (Open Weather API allows only 5 days) and give a call to https://api.openweathermap.org/data/2.5/onecall/timemachine . The `hourly` attribute of response gives the weather report for each hour of past 5 days (24*5 hours). 
6. Pass the dataset of temperature,humidity, precipitation to `Chart` along with the canvas tag defined in HTML. Your charts are rendered.

### Caution
I don't have a billing account of GCP. Therefore, the places may or may not be suggested in autocomplete based on daily free quota. Don't worry, you will still be able to get weather forecast of a place if you type a correct city name.

### Output
Try with places which have heavy rainfall so that you don't get blank precipitation chart. 
Eg. Mawsynram , Cherrapunji
