# Lovelace animated weather card for WRAL Weather

This is a modified copy of the Lovelace animated weather card from [bramkragten](https://github.com/bramkragten/weather-card) to work with the [WRAL Weather custom component for Home Assistant](https://github.com/tommyjlong/wral_weather).

For details, check out this [README.md](https://github.com/tommyjlong/wral-weather-card/blob/master/README.md).

An example (without the animation) of what the card would look like:
![Weather Card](https://github.com/tommyjlong/wral-weather-card/blob/master/wral-weather-card.jpg?raw=true)

# Installation:
The recommended way to install is to use HACS. Alternatively, this can be manually installed.

Go to the HACS Settings, and under ADD CUSTOM RESPOSITORY, paste ```https://github.com/tommyjlong/wral-weather-card ```, and chose ```Plugin``` for the Category.  Hit save, and a new entry titled **[plugin]
tommyjlong/wral-weather-card** should be created under CUSTOM REPOSITORY.  Click on the new entry and a page should appear which will allow you to install this.  Make sure to follow the instructions at the very bottom of the page for adding the url and type to the lovelace configuration.

Be sure to add the resources in your lovelace config per the instructions at the bottom of the HACS page.

* If you want to manually install, check out this [README.md](https://github.com/tommyjlong/wral-weather-card/blob/master/README.md).

# Lovelace Configuration:

When adding a card, make the type `custom:wral-weather-card`:

```yaml
type: custom:wral-weather-card
entity: weather.yourWralWeatherEntity
name: Optional-name
icons: "/local/DIRECTORY_X/wral-weather-card/icons/"
current: true
details: false
forecast: true
```
- ```name:``` This is optional, but if present will show in the card.
- ```icons:``` Unlike the Original Weather Card which gave the option to use the icons locally, for the WRAL Weather Card it is REQUIRED.  For HACS: Set this to ``icons: "/local/community/weather-card/icons/"```
- ```current:``` Show the current weather icon, the current temperature and title
- ```details:``` Show the details about the current WRAL weather observations, such as wind, and humidity.
- ```forecast:``` Show the 5 day forecast.

If you want to show the sunrise and sunset times, make sure the `sun` component is enabled:

```yaml
# Example configuration.yaml entry
sun:
```
