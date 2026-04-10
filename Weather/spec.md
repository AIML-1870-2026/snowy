# Weather Dashboard

## Overview
A static webpage that displays real-time weather information using the OpenWeatherMap API. Users can search for any city and view current conditions along with a weekly forecast.

## Features
- **City Search**: Text input for users to search any city worldwide
- **Real-Time Weather**: Current weather conditions fetched from OpenWeatherMap API
- **Temperature Unit Toggle**: Option to switch between Celsius and Fahrenheit
- **Current Conditions Display**:
  - Temperature
  - Feels Like
  - Humidity
  - Wind Speed
  - UV Index
  - Visibility
- **Weekly Forecast**: 7-day forecast with daily conditions

## Technical Requirements

### API
- OpenWeatherMap API integration
- API key stored securely (not hardcoded in production)
- HTTPS requests for all API calls

### User Experience

- Loading states while fetching data
- Error handling for invalid cities or API failures
- Input validation for city search

### Data Persistence
- Local storage to remember:
  - Last searched city
  - Preferred temperature unit

### Performance
- Debounce search input to limit API calls
- Cache recent searches to reduce redundant requests

### Accessibility
- Keyboard navigation support
- Appropriate ARIA labels
- Sufficient color contrast
