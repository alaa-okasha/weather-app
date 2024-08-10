# Weather App

## Description
A simple web application that allows users to check the current weather conditions of any city. The app fetches data from the OpenWeatherMap API and displays the weather details such as temperature, humidity, and wind speed. Users can search for a city and see the corresponding weather information.

## Features
- Search for a city's weather by name.
- Display current temperature, humidity, and wind speed.
- Display appropriate weather icons based on the weather conditions.
- Show an error message for invalid city names.

## Installation
To run this project locally, follow these steps:

1. Clone the repository:
    ```bash
    git clone https://github.com/alaa-okasha/weather-app.git
    ```

2. Navigate to the project directory:
    ```bash
    cd weather-app
    ```

3. Open `index.html` in your web browser.

## Usage
1. Open the `index.html` file in your web browser.
2. Enter a city name in the search input field.
3. Click the search button or press Enter to fetch the weather data.
4. View the weather information displayed on the card.

## Code Explanation

### HTML
The HTML structure includes a search input, an error message section, and a weather display section with details like temperature, city name, humidity, and wind speed.

### CSS
The styles for this app are included in the `style.css` file, which is linked in the HTML. The fonts are imported from Google Fonts.

### JavaScript
The JavaScript code includes:
- An API key and URL for fetching weather data.
- Functions to fetch and display weather data based on the city name.
- Event listeners for the search button and the Enter key.

Here's a snippet of the JavaScript code used to fetch and display weather data:
```javascript
const apiKey = "e7e2cda6bbd01f61c5ac4e93c5ed26e3";
const apiUrl = "https://api.openweathermap.org/data/2.5/weather?units=metric&q=";

const searchBox = document.querySelector('.search input');
const searchBtn = document.querySelector('.search button');
const weatherIcon = document.querySelector('.weather-icon');

async function checkWeather(city) {
    const response = await fetch(apiUrl + city + `&appid=${apiKey}`);

    if(response.status == 404){
        document.querySelector('.error').style.display = "block";
        document.querySelector('.weather').style.display = "none";
    } else {
        const data = await response.json();

        document.querySelector('.city').innerHTML = data.name;            
        document.querySelector('.temp').innerHTML = Math.round(data.main.temp) + '°C';            
        document.querySelector('.humidity').innerHTML = data.main.humidity + '%';            
        document.querySelector('.wind').innerHTML = data.wind.speed + ' Km/h';            

        if(data.weather[0].main == 'Clouds'){
            weatherIcon.src = 'images/clouds.png';
        } else if (data.weather[0].main == 'Clear'){
            weatherIcon.src = 'images/clear.png';
        } else if (data.weather[0].main == 'Rain'){
            weatherIcon.src = 'images/rain.png';
        } else if (data.weather[0].main == 'Drizzle'){
            weatherIcon.src = 'images/drizzle.png';
        } else if (data.weather[0].main == 'Mist'){
            weatherIcon.src = 'images/mist.png';
        }

        document.querySelector('.weather').style.display = 'block';
        document.querySelector('.error').style.display = "none";
    }
}

searchBtn.addEventListener('click', () => {
    checkWeather(searchBox.value);
});

document.addEventListener('keydown', (e) => {
    if (e.key === 'Enter') {
        checkWeather(searchBox.value);
    }
}); 
```

## Technologies Used
- HTML
- CSS
- JavaScript
- OpenWeartherMap API

## Contributing
Contributions are welcome! Please fork the repository and create a pull request with your changes.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Contact
If you have any questions or suggestions, feel free to reach out:

- Alaa okasha
- [Email](mailto:y3040a@gmail.com)
- [GitHub](https://github.com/alaa-okasha)
