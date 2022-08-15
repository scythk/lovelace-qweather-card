# Qweather card
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg?style=for-the-badge)](https://github.com/hacs/integration)

Added Qweather support with hourly forecast compatibility.

Works well with [和风天气 Home Assistant 插件](https://github.com/cheny95/qweather).

Originally created for the [old UI](https://community.home-assistant.io/t/custom-ui-weather-state-card-with-a-question/23008) converted by @arsaboo and @ciotlosm to [Lovelace](https://community.home-assistant.io/t/custom-ui-weather-state-card-with-a-question/23008/291) and now converted to Lit to make it even better.

This card uses the awesome [animated SVG weather icons by amCharts](https://www.amcharts.com/free-animated-svg-weather-icons/).

![Weather Card](https://github.com/bramkragten/custom-ui/blob/master/weather-card/weather-card.gif?raw=true)

Thanks for all picking this card up.

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

1. Download the [weather-card.js](https://raw.githubusercontent.com/bramkragten/weather-card/v1.2.0/dist/weather-card.js) to `/config/www/community/lovelace-qweather-card/`. (or an other folder in `/config/www/`)
2. Save, the [amCharts icons](https://www.amcharts.com/free-animated-svg-weather-icons/) (The contents of the folder "animated") under `/config/www/community/lovelace-qweather-card/icons/` (or an other folder in `/config/www/`)
3. If you use Lovelace in storage mode, and want to use the editor, download the [weather-card-editor.js](https://raw.githubusercontent.com/bramkragten/weather-card/v1.2.0/dist/weather-card-editor.js) to `/config/www/community/lovelace-qweather-card/`. (or the folder you used above)

Add the following to resources in your lovelace config:

```yaml
resources:
  - url: /local/community/lovelace-qweather-card/qweather-card.js
    type: module
```

## Configuration:

And add a card with type `custom:qweather-card`:

```yaml
type: custom:qweather-card
entity: weather.yourweatherentity
name: Optional name
```

If you want to use your local icons add the location to the icons:

```yaml
type: custom:qweather-card
entity: weather.yourweatherentity
icons: "/local/community/lovelace-qweather-card/icons/"
```

You can choose which elements of the weather card you want to show:

The 3 different rows, being:

- The current weather icon, the current temperature and title
- The details about the current weather
- The X day forecast or hourly forecast

```yaml
type: custom:qweather-card
entity: weather.yourweatherentity
current: true
details: false
forecast: true
hourly_forecast: false
number_of_forecasts: 5
```

If you want to show the sunrise and sunset times, make sure the `sun` component is enabled:

```yaml
# Example configuration.yaml entry
sun:
```

### Qweather:

See [和风天气 Home Assistant 插件](https://github.com/cheny95/qweather) for details.

```yaml
# Example configuration.yaml entry
weather:
  - platform: qweather
    name: WEATHER_ENTITY_NAME
    api_key: YOUR_API_KEY
    location: YOUR_LOCATION
    default: 7
    scan_interval: 600
```
