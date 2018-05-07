# HTML 5 APIs

## Lesson Objectives

1. Explain what HTML 5 APIs are
1. List some common APIs and what they do

## Explain what HTML 5 APIs are

HTML5 means the new HTML elements that have recently been added, but it also means a collection of advanced functionality that browsers are expected to have.  A decent summary can be found [here](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5).

## List some common APIs and what they do

### Semantics

- Sections and outlines in HTML5: organizational tags that don't effect layout
- Using HTML5 audio and video: easily embed audio/video in a web page
- Forms improvements: new types of inputs + validation

### Performance and Integration

- Web Workers: put long running processes in the background, so your site doesn't slow down
- XMLHttpRequest level 2: making ajax calls is syntactically easier than ever.  [You don't even really need jQuery for it anymore](http://youmightnotneedjquery.com/)
- History API: Manipulate the browser history with JS.  Make it seem like the user has visited a new page, when they haven't
- Drag and drop: allows you to drag and drop items within and between sites
- Focus management in HTML: lets you see if an element has been focused on.  Lets you see which element is focused on
- Fullscreen API: take over the screen
- Online and offline events: see when the user has lost/regained connection

### Connectivity

- Web Sockets: create a permanent connection between the page/server for extra fast communication
- WebRTC: video conferencing in the browser

### Device Access

- Using the Camera API: use a camera to get instant avatar icons... or spy on your exes
- Touch events: for mobile/tablet devices
- Using geolocation: again, great for spying on exes
- Detecting device orientation: good for mobile/tablet devices being held in landscape/portrait mode.  Not so good for desktops

### Offline and Storage

- Offline resources: The application cache: allows you to use the site somewhat without connectivity
- WHATWG client-side session and persistent storage (aka DOM storage): better cookies
- IndexedDB: kinda like MongoDB, but for storing stuff client-side
- Using files from web applications: access local files from a web app

### Styling

- New background styling features: shadows, multiple backgrounds, filters
- More fancy borders: curved borders, images for borders
- Animating your style: transitions and animations
- Typography improvement: custom fonts!
- New presentational layouts: flex-box does what you always wanted to do, but couldn't

### 3D Graphics

- Canvas: Good for "raster" (or pixel) graphics/animations/games. Draw like Microsoft Paint, re-make NES games, etc
- SVG: Good for "vector" (or math-based) graphics/animations/games.  Every graph you see online now uses this (probably with the D3.js lib)
- WebGL - 3D graphics support!!!!  Fortnite in the browser
