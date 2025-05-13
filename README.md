<!DOCTYPE html>
<html>
<head>
  <title>Interactive US Map with Pings</title>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
  <!-- Leaflet CSS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
  
  <!-- Leaflet JS -->
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
  
  <style>
    #map {
      height: 100vh;
    }
  </style>
</head>
<body>

<div id="map"></div>

<script>
  // Initialize the map
  var map = L.map('map').setView([40.54, -74.52], 11); // Centered around NJ

  // Add OpenStreetMap tiles
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; OpenStreetMap contributors'
  }).addTo(map);

  // Marker 1: 207 Ronan Way, NJ 08853 (approximate lat/lon)
  L.marker([40.5604, -74.5449])
    .addTo(map)
    .bindPopup('<b>207 Ronan Way</b><br>South Bound Brook, NJ 08853');

  // Marker 2: 800 Apgar Dr, NJ 08873 (approximate lat/lon)
  L.marker([40.5351, -74.5239])
    .addTo(map)
    .bindPopup('<b>800 Apgar Dr</b><br>Somerset, NJ 08873');
</script>

</body>
</html>
