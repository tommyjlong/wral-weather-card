# Lovelace animated weather card for WRAL Weather

This is a modified copy of the Lovelace animated weather card from [bramkragten](https://github.com/bramkragten/weather-card) to work with the [WRAL Weather custom component for Home Assistant](https://github.com/tommyjlong/wral_weather).

This card uses the [animated SVG weather icons by amCharts](https://www.amcharts.com/free-animated-svg-weather-icons/) but also adds an animated fog.svg from [Jason Parthum](https://community.home-assistant.io/t/animated-weather-icons-svg-for-all-dark-sky-values/150702) that has been modified.

An example (without the animation) of what the card would look like:
![Weather Card](https://github.com/tommyjlong/wral-weather-card/blob/master/wral-weather-card.jpg?raw=true)

# Installation:
The recommended way to install is to use HACS. Alternatively, this can be manually installed.

**Note:** The Original Weather Card supports using the Lovelace UI in "Storage" mode.  It uses the weather-card.editor for this which is NOT being supported for the wral-weather-card.

**Note:** The Original Weather Card allowed you to get some of its resources over the internet in what it called a "Hosted" based installation.  This is NOT supported for the wral-weather-card.
## HACS
Go to the HACS Settings, and under ADD CUSTOM RESPOSITORY, paste ```https://github.com/tommyjlong/wral-weather-card ```, and chose ```Plugin``` for the Category.  Hit save, and a new entry titled **[plugin]
tommyjlong/wral-weather-card** should be created under CUSTOM REPOSITORY.  Click on the new entry and a page should appear which will allow you to install this.  Make sure to follow the instructions at the very bottom of the page for adding the url and type to the lovelace configuration.

## Manual:
1. Download the [wral-weather-card.js](https://github.com/tommyjlong/wral-weather-card/blob/master/dist/wral-weather-card.js) to `HACONFIGDIR/www/custom-lovelace/wral-weather-card/` (or in some other folder under `/HACONFIGDIR/www/`).
2. Save, the [Animated Icons](https://github.com/tommyjlong/wral-weather-card/tree/master/dist/icons/) to the `HACONFIGDIR/www/custom-lovelace/weather-card/icons/` directory (or in some other directory in `HACONFIGDIR/www/`)

Add the following to resources in your lovelace config:

```yaml
resources:
  - url: /local/custom-lovelace/wral-weather-card/wral-weather-card.js
    type: module
```

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

# Known Quirks
After around 6:00pm, WRAL stops sending the current day's forecast high temperature.  This results in the card showing a blank high temperature for the first day's forecast.
# Changes to Orginal Weather-Card (v1.4.1)
- Adds animated "fog.svg" to icons.
- Changes Class of WeatherCard to WRALWeatherCard
- Removes visibility as WRAL does not provide this.
- Changed precipitation to precipitation probability as WRAL provides precipitation forecasts in probability percentages and not amounts.
- Slight modifications to Title styling.
- Changes default icon location to /local/community/wral-weather-card/icons/ {TBF}

# Credits
- Original Weather Card: This is a modified copy of the Lovelace animated weather card from [brankragten](https://github.com/bramkragten/weather-card) to work with the [WRAL Weather custom component](https://github.com/tommyjlong/wral_weather).
- amCharts: Except where noted, the animated icons were created by amCharts (https://www.amcharts.com/)
and is licensed under Creative Commons Attribution 4.0 International Public License:
https://creativecommons.org/licenses/by/4.0/
If in doubt, email amCharts at contact@amcharts.com
- fog animated icon: Original from  [Jason Parthum](https://community.home-assistant.io/t/animated-weather-icons-svg-for-all-dark-sky-values/150702) that has been modified slightly.

