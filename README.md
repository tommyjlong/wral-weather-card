# Lovelace animated weather card for WRAL Weather

This is a modified copy of the Lovelace animated weather card from [brankragten] (https://github.com/bramkragten/weather-card) to work with the [WRAL Weather custom component](https://github.com/tommyjlong/wral_weather).

This card also uses the awesome [animated SVG weather icons by amCharts](https://www.amcharts.com/free-animated-svg-weather-icons/).
It also adds an animated fog svg from [Jason Parthum](https://community.home-assistant.io/t/animated-weather-icons-svg-for-all-dark-sky-values/150702) that has been modified.

![Weather Card](https://github.com/bramkragten/custom-ui/blob/master/weather-card/weather-card.gif?raw=true)

## Installation:

You have 2 options, hosted or self hosted (manual). The first option needs internet and will update itself.

### If you are using Firefox:

Firefox < 66 does not support all the needed functions yet for the editor.
You change this by enabling `javascript.options.dynamicImport` in `about:config`.
Or use the version without the editor: [Version without editor](https://raw.githubusercontent.com/bramkragten/custom-ui/58c41ad177b002e149497629a26ea10ccfeebcd0/weather-card/weather-card.js)

# Hosted:

Add the following to resources in your lovelace config:

```yaml
- url: https://cdn.jsdelivr.net/gh/bramkragten/weather-card/dist/weather-card.min.js
  type: module
```

# Manual:

1. Download the [weather-card.js](https://raw.githubusercontent.com/bramkragten/weather-card/v1.2.0/dist/weather-card.js) to `/config/www/custom-lovelace/weather-card/`. (or an other folder in `/config/www/`)
2. Save, the [amCharts icons](https://www.amcharts.com/free-animated-svg-weather-icons/) (The contents of the folder "animated") under `/config/www/custom-lovelace/weather-card/icons/` (or an other folder in `/config/www/`)
3. If you use Lovelace in storage mode, and want to use the editor, download the [weather-card-editor.js](https://raw.githubusercontent.com/bramkragten/weather-card/v1.2.0/dist/weather-card-editor.js) to `/config/www/custom-lovelace/weather-card/`. (or the folder you used above)

Add the following to resources in your lovelace config:

```yaml
resources:
  - url: /local/custom-lovelace/weather-card/weather-card.js
    type: module
```

## Configuration:

And add a card with type `custom:weather-card`:

```yaml
type: custom:weather-card
entity: weather.yourweatherentity
name: Optional name
```

If you want to use your local icons add the location to the icons:

```yaml
type: custom:weather-card
entity: weather.yourweatherentity
icons: "/local/custom-lovelace/weather-card/icons/"
```

You can choose wich elements of the weather card you want to show:

The 3 different rows, being:

- The current weather icon, the current temperature and title
- The details about the current weather
- The 5 day forecast

```yaml
type: custom:weather-card
entity: weather.yourweatherentity
current: true
details: false
forecast: true
```

If you want to show the sunrise and sunset times, make sure the `sun` component is enabled:

```yaml
# Example configuration.yaml entry
sun:
```

# Known Quirks
After around 6:00pm, WRAL stops sending the current day's forecast high temperature.  This results in the card showing a blank high temperature.
# Changes to Orginal Weather-Card (v1.4.1)
- Adds animated "fog.svg" to icons.
- Changes Class of WeatherCard to WRALWeatherCard
- Removes visibility as WRAL does not provide this.
- Changed precipitation to precipitation probability as WRAL provides precipitation forecasts in probability percentages and not amounts.
- Slight modifications to Title styling.
- Changes default icon location to /local/community/wral-weather-card/icons/ {TBF}

# Credits
- Original Weather Card: This is a modified copy of the Lovelace animated weather card from [brankragten] (https://github.com/bramkragten/weather-card) to work with the [WRAL Weather custom component](https://github.com/tommyjlong/wral_weather).
- amCharts: Except where noted, the animated icons were created by amCharts (https://www.amcharts.com/)
and is licensed under Creative Commons Attribution 4.0 International Public License:
https://creativecommons.org/licenses/by/4.0/
If in doubt, email amCharts at contact@amcharts.com
- fog animated icon: Original from  [Jason Parthum](https://community.home-assistant.io/t/animated-weather-icons-svg-for-all-dark-sky-values/150702) that has been modified.

