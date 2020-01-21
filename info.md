# Lovelace Animated Weather Card for WRAL Weather

This is a modified copy of the Lovelace animated weather card from [bramkragten](https://github.com/bramkragten/weather-card) to work with the [WRAL Weather custom component for Home Assistant](https://github.com/tommyjlong/wral_weather).

For details, check out this [README.md](https://github.com/tommyjlong/wral-weather-card/blob/master/README.md).

An example (without the animation) of what the card would look like:
![Weather Card](https://github.com/tommyjlong/wral-weather-card/blob/master/wral-weather-card.jpg?raw=true)

# Installation:
## HACS

- Go to the HACS Settings, and under ADD CUSTOM RESPOSITORY, paste ```https://github.com/tommyjlong/wral-weather-card ```, and chose ```Plugin``` for the Category.  Hit save, and a new entry titled **[plugin]
tommyjlong/wral-weather-card** should be created under CUSTOM REPOSITORY.  
- Click on the new entry and a page should appear which will allow you to install this.  
- Make sure to follow the instructions at the very bottom of the page for adding the url and type to the lovelace configuration.

## Manually: 
If you want to manually install, check out this [README.md](https://github.com/tommyjlong/wral-weather-card/blob/master/README.md).

# Lovelace Configuration:

When adding a card, make the type `custom:wral-weather-card`:

```yaml
type: custom:wral-weather-card
entity: weather.yourWralWeatherEntity
name: Optional-name
icons: "/local/DIRECTORY_X/wral-weather-card/icons/"
current: true
details: true
forecast: true
```
- ```name:``` This is optional, but if present will show on the face of the card.
- ```icons:``` Location of the icons.  Unlike the Original Weather Card which gave the option to use the icons locally, for the WRAL Weather Card it is REQUIRED.  For HACS: Set this to ```icons: "/local/community/wral-weather-card/icons/"```
- ```current:``` Show the current weather icon, the current temperature and title
- ```details:``` Show the details about the current WRAL weather observations, such as wind, and humidity.
- ```forecast:``` Show the 5 day forecast.

If you want to show the sunrise and sunset times, make sure the `sun` component is enabled:

```yaml
# Example configuration.yaml entry
sun:
```
