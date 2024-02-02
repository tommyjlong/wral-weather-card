# Lovelace Animated Weather Card for WRAL Weather

A Lovelace animated weather card to work with the [WRAL Weather custom integration for Home Assistant](https://github.com/tommyjlong/wral_weather).</br>

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)</br>
This is a modified copy of the Lovelace animated weather card from [bramkragten](https://github.com/bramkragten/weather-card). 

An example of what the card would look like (less the animation):</br>
![Weather Card](https://github.com/tommyjlong/wral-weather-card/blob/master/wral-weather-card.jpg?raw=true)

# Installation:
The recommended way to install is to use HACS. Alternatively, this can be manually installed.

**Note:** The Original Weather Card allowed you to get some of its resources over the internet in what it called a "Hosted" based installation.  This is NOT supported for the wral-weather-card.

## HACS
- Go to the HACS Settings, and under ADD CUSTOM RESPOSITORY, paste ```https://github.com/tommyjlong/wral-weather-card ```, and chose ```Plugin``` for the Category.  Hit save, and a new entry titled **[plugin]
tommyjlong/wral-weather-card** should be created under CUSTOM REPOSITORY.  
- Click on the new entry and a page should appear which will allow you to install this.  
- Make sure to follow the instructions at the very bottom of the page for adding the url and type to the lovelace configuration.

## Manual:
1. Download the [wral-weather-card.js](https://github.com/tommyjlong/wral-weather-card/blob/master/dist/wral-weather-card.js) and its companion [weather-card-editor.js](https://github.com/tommyjlong/wral-weather-card/blob/master/dist/wral-weather-card-editor.js) files to `HACONFIGDIR/www/custom-lovelace/wral-weather-card/` (or in some other folder under `/HACONFIGDIR/www/`).
2. Save, the [Animated Icons](https://github.com/tommyjlong/wral-weather-card/tree/master/dist/icons/) to the `HACONFIGDIR/www/custom-lovelace/weather-card/icons/` directory (or in some other directory in `HACONFIGDIR/www/`)

Add the following to resources in your lovelace config (if using YAML mode):

```yaml
resources:
  - url: /local/custom-lovelace/wral-weather-card/wral-weather-card.js
    type: module
```

If using the UI (instead of YAML mode), goto Configuration->Lovelace Dashboards; Click on 3-dots  and click on "Resources"
and click on "+ Add Resource" and add this url and resource type as "Javascript Module".

# Lovelace Configuration:
The WRAL Weather Card can be configured using the UI Editor, or using the old fashioned YAML configuration.

## UI Card Editor
When using the HA UI to add this card, get into the Editor mode (click on dashboard's upper-right 3-dots and click on "Edit Dashboard" and click "+ ADD CARD", and scroll to the bottom and click on "MANUAL".
A dialog box will show up where you should enter the following (`entity` and `icons` are user specific):
```
type: 'custom:wral-weather-card'
entity: weather.yourWralWeatherEntity
icons: "/local/custom-lovelace/wral-weather-card/icons/"
```
At this point, the WRAL Weather Card Editor should be rendered and in the "SHOW CODE EDITOR" mode.  You can continue to provide YAML based configuration here, or click on "SHOW VISUAL EDITOR".
Here is an example using the SHOW VISUAL EDITOR. 
![Weather Card Editor](https://github.com/tommyjlong/wral-weather-card/blob/master/wral-weather-card-editor.png?raw=true)

An explaination for each parameter is discussed below in the YAML Config section.
## YAML Config
When adding a card, make the type `custom:wral-weather-card`:

```yaml
type: custom:wral-weather-card
entity: weather.yourWralWeatherEntity
name: Optional-name
icons: "/local/DIRECTORY_X/wral-weather-card/icons/"
current: true
details: true
forecast: true
forecast_type: daily
number_of_forecasts: 5
```
- ```name:``` This is optional, but if present will show on the face of the card. (Example "Raleigh").
- ```icons:``` Location of the icons.  By default, the icons are located where HACS places them which is at ```/local/community/wral-weather-card/icons/```.  Unlike the Bramkragten Weather Card which gave the option to use the icons locally or hosted remotely, the WRAL Weather Card requires the icons to be local and stored in a web accessible directory specified by this parameter.
- ```current:``` Show the current weather icon, the current temperature and title.
- ```details:``` Show the details about the current WRAL weather observations, such as wind, and humidity.
- ```forecast:``` Show the daily or hourly forecast.
- `forecast_type:` Which forcast to show, either `daily` or `hourly`
- `number of forecasts:`  The number of forecasts to show.

If you want to show the sunrise and sunset times, make sure the `sun` component is enabled:

```yaml
# Example configuration.yaml entry
sun:
```

# Known Limitations/Quirks
- Starting in Home Assistant version 2023.9, the way weather forecasts are retrieved by Lovelace cards was completely changed and restructured.   This card was updated to support this and no longer supports the legacy way prior to this version.
- After around 6:00pm, WRAL stops sending the current day's forecast high temperature.  This results in the card showing a blank high temperature for the first day's forecast.
- Not all the animated SVG files are used.  This is due to the the WRAL Weather custom integration support for the standard hui-weather-forecast-card which has limited mappings of conditions to icons.
# Changes to Orginal Bramkragten Weather-Card 
- Adds animated "fog.svg" to icons.
- Changes Class of WeatherCard to WRALWeatherCard
- Changed precipitation to precipitation probability as WRAL provides precipitation forecasts in probability percentages and not amounts.
- Slight modifications to Title styling.
- Changes default icon location to /local/community/wral-weather-card/icons/ 
- Add more bottom margin to .current to prevent rain drops from bleeding over humidity.

# Credits
- Original Weather Card: This is a modified copy of the Lovelace animated weather card from [bramkragten](https://github.com/bramkragten/weather-card) to work with the [WRAL Weather custom component](https://github.com/tommyjlong/wral_weather).
- amCharts: Except where noted, the animated icons were created by amCharts (https://www.amcharts.com/) (https://www.amcharts.com/free-animated-svg-weather-icons/)
and is licensed under Creative Commons Attribution 4.0 International Public License:
https://creativecommons.org/licenses/by/4.0/
If in doubt, email amCharts at contact@amcharts.com
- A fog animated icon was added and modified. Original from:  [Jason Parthum](https://community.home-assistant.io/t/animated-weather-icons-svg-for-all-dark-sky-values/150702).

