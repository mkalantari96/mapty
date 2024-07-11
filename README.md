# mapty // Map your workouts

Welcome to **mapty**, an interactive web application to map and track your workouts! This project allows you to log running and cycling workouts with details like distance, duration, and other statistics. It provides an easy-to-use interface to visualize your workouts on a map.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Features](#features)
- [File Structure](#file-structure)

## Installation

1. **Clone the repository:**

   ```sh
   git clone https://github.com/your-username/mapty.git
   ```

2. **Navigate to the project directory:**

   ```sh
   cd mapty
   ```

3. **Open `index.html` in your preferred web browser:**
   ```sh
   open index.html
   ```
   Or simply double-click the `index.html` file.

## Usage

1. **Add a Workout:**

   - Click on the map to add a workout.
   - A form will appear on the sidebar. Select the type of workout (Running or Cycling).
   - Fill in the distance, duration, and other fields.
   - Submit the form to log the workout.

2. **View Workouts:**
   - Logged workouts will appear in the sidebar list.
   - Clicking on a workout in the sidebar will highlight its location on the map.

## Features

- **Interactive Map:** Uses Leaflet.js to provide a dynamic map interface.
- **Responsive Design:** Works seamlessly across various device sizes.
- **Workout Logging:** Log workouts with details like distance, duration, cadence, and elevation gain.
- **Persistent Data:** Workouts are saved in local storage, so they persist across sessions.

## File Structure

- **index.html:** The main HTML file containing the structure of the application.
- **style.css:** The CSS file for styling the application.
- **script.js:** The JavaScript file containing the logic for interacting with the map and handling workout data.

### index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <!-- Meta and Link Tags -->
  </head>
  <body>
    <!-- Sidebar and Map Container -->
    <div class="sidebar">
      <img src="logo.png" alt="Logo" class="logo" />
      <ul class="workouts">
        <form class="form hidden">
          <!-- Form Fields -->
        </form>
      </ul>
    </div>
    <div id="map"></div>
  </body>
</html>
```

### style.css

```css
:root {
  --color-brand--1: #ffb545;
  --color-brand--2: #00c46a;
  /* More Variables */
}

* {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

/* General Styles */
body {
  font-family: "Manrope", sans-serif;
  /* More Styles */
}

/* Sidebar and Form Styles */
.sidebar {
  flex-basis: 50rem;
  background-color: var(--color-dark--1);
}

/* Map Styles */
#map {
  flex: 1;
  height: 100%;
}
```

### script.js

```js
"use strict";

const form = document.querySelector(".form");
const containerWorkouts = document.querySelector(".workouts");
const inputType = document.querySelector(".form__input--type");
const inputDistance = document.querySelector(".form__input--distance");
const inputDuration = document.querySelector(".form__input--duration");
const inputCadence = document.querySelector(".form__input--cadence");
const inputElevation = document.querySelector(".form__input--elevation");

class Workout {
  date = new Date();
  id = (Date.now() + "").slice(-10);
  clicks = 0;

  constructor(coords, distance, duration) {
    this.coords = coords;
    this.distance = distance;
    this.duration = duration;
  }

  _setDescription() {
    const months = [
      "January",
      "February",
      "March",
      "April",
      "May",
      "June",
      "July",
      "August",
      "September",
      "October",
      "November",
      "December",
    ];
    this.description = `${this.type[0].toUpperCase()}${this.type.slice(1)} on ${
      months[this.date.getMonth()]
    } ${this.date.getDate()}`;
  }

  click() {
    this.clicks++;
  }
}

// More code...
```
