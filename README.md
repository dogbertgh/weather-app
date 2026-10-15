# Weather App

A simple, dependency-free web app that shows the current temperature, a 24-hour chart, a 7-day forecast, and active National Weather Service alerts for your location or any city you search.

## Features

- **Current conditions** – temperature, weather icon, and description for your location (via browser geolocation) or any searched city. Falls back to New York City if location access is denied.
- **°F / °C toggle** – switches all temperatures instantly; your choice is remembered between visits.
- **7-day forecast** – daily icon, high/low, chance of rain, and a bar showing each day's temperature range relative to the week.
- **Next 24 hours chart** – temperature line with the high and low labeled, condition icons every 3 hours, and a separate chance-of-rain panel. Hover (or focus the chart and use the arrow keys) for hour-by-hour details, or open **Show as table** for every value.
- **NWS watches, warnings & advisories** – for US locations, shown below the forecast, color-coded by severity and sorted most severe first. Expand an alert for the full description and safety instructions. Times are shown in the location's timezone.
- **Auto-refresh** – alerts refresh every 2 minutes and the forecast every 15 minutes. Refreshing pauses while the tab is hidden and catches up when you return.

## Running it

Requires [Node.js](https://nodejs.org/) (any recent version). There are no packages to install.

```bash
npm start
```

Then open http://localhost:3000. To use a different port:

```bash
PORT=8080 npm start
```

## Data sources

Weather data is fetched directly from the browser; the Node server only serves the page.

- **[Open-Meteo](https://open-meteo.com/)** – current conditions, hourly and daily forecasts, and city search (geocoding). Free, no API key, intended for non-commercial use.
- **[National Weather Service API](https://www.weather.gov/documentation/services-web-api)** – active alerts. Covers the US and its territories only; alerts are simply hidden for other locations.

> **Note:** This app is a convenience, not an official warning system. Always check [weather.gov](https://www.weather.gov) or local authorities for life-safety alerts.

## Project structure

```
server.js           Minimal Node static file server (no dependencies)
public/index.html   The entire app: markup, styles, and JavaScript
package.json        Defines the `npm start` script
.devcontainer/      VS Code dev container (Node 24 + Claude Code)
```

## Development container

The repo includes a [VS Code dev container](https://code.visualstudio.com/docs/devcontainers/containers) with Node 24 and [Claude Code](https://claude.com/claude-code) preinstalled. With Docker and VS Code installed, open the folder in VS Code and choose **Reopen in Container**, then run `npm start` in the container's terminal; VS Code will offer to forward port 3000.

The dev container setup comes from [tim-sha256/claude-in-docker](https://github.com/tim-sha256/claude-in-docker) ([write-up](https://timsh.org/claude-inside-docker/)).
