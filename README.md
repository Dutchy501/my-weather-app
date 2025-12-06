# my-weather-app
Simple app that checks the weather based on a provided zip code

function main():
    zip_code = prompt("Enter the ZIP code you wish to check: ")

    weather_data = fetch_weather_for_zip(zip_code)
    if weather_data is error:
        print("Unable to retrieve weather for that ZIP code.")
        exit with error

    conditions = extract_conditions(weather_data)
    display_conditions(conditions)
    exit successfully


function fetch_weather_for_zip(zip_code):
    # Call a free weather API with the ZIP code as a parameter
    # Return the raw JSON or data structure
    response = HTTP_GET("https://weather-api.example?zip=" + zip_code)
    return response


function extract_conditions(weather_data):
    # Pull out only what we care about
    location_name = weather_data.location.name
    temp = weather_data.current.temperature
    wind = weather_data.current.wind_speed
    alerts = weather_data.alerts
    condition = weather_data.current.description

    return (location_name, temp, wind, condition, alerts)


function display_conditions(conditions):
    (location_name, temp, wind, condition, alerts) = conditions

    print("Location:", location_name)
    print("Temperature:", temp)
    print("Condition:", condition)
    print("Wind:", wind)

    if alerts is not empty:
        print("Alerts:")
        for alert in alerts:
            print(" -", alert.title)

